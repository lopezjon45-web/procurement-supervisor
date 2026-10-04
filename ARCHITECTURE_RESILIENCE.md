# Architecture Resilience Foundation

## Document status

Accepted Stage 0 foundation (AQ-009, closed); see [ROADMAP.md](ROADMAP.md).
It defines target behavior. It does not certify that the current runtime
implements these interfaces, endpoints, failure modes, or transaction mechanisms.
Approval boundaries remain governed by [AI_SUPERVISOR.md](AI_SUPERVISOR.md) and
[APPROVAL_QUEUE.md](APPROVAL_QUEUE.md).

## Purpose

Define a concrete architecture that remains coherent when external services disappear.

The procurement core must remain meaningful under degraded conditions. Loss of
an optional service may reduce capability, latency, freshness, or reachability,
but it must not:

- corrupt authoritative state;
- change the meaning of evidence;
- silently spend quota or money;
- promote unknown information into facts;
- silently broaden authorization;
- create duplicate transactions;
- make the service claim a capability it no longer has.

## Authoritative Spine

The authoritative runtime spine is intentionally small:

1. Procurement application/core.
2. PostgreSQL/Neon authoritative persistence.

PostgreSQL owns durable procurement state. Optional systems may cache or project
it, but they do not become independent sources of procurement truth.

If PostgreSQL is unavailable, the service must fail explicitly for authoritative
procurement operations rather than silently treating Redis, local files, or stale
process memory as a second database.

Database high availability, if needed later, must be solved at the
database/replication layer rather than by promoting an accelerator into authority.

## Dependency Classes

### Tier A — Authoritative Core

- procurement application/core;
- PostgreSQL/Neon.

Loss materially reduces the service. State-changing procurement and authoritative
evidence operations must stop safely if the database is unavailable.

### Tier B — Functional Providers

Examples:

- discovery providers;
- verification/browser providers;
- supplier APIs;
- payment providers;
- external authentication issuers.

Loss removes a capability but must leave the remaining procurement core coherent.

### Tier C — Accelerators and Transport

Examples:

- Redis;
- ngrok;
- CDN;
- background workers;
- queue infrastructure;
- observability.

Loss may affect latency, public reachability, scheduling, or convenience. It must
not alter procurement truth.

## Dependency-Minimization Rule

A new external runtime service is prohibited unless it provides a measured
capability that cannot reasonably be provided by the current application/Postgres
architecture.

Every proposal must answer:

- Purpose.
- Why the current stack is insufficient.
- Which dependency tier it belongs to.
- What authoritative state it owns, if any.
- What happens when it is unavailable.
- How it can be replaced.
- Security impact.
- Cost and operational burden.
- Rollback plan.

## Ports and Adapters

Business/domain logic must depend on capabilities, not vendor SDKs.

Core-facing interfaces should be concepts such as:

- IntelligenceRepository;
- DiscoveryProvider;
- VerificationProvider;
- TransactionProvider;
- AuthenticationProvider;
- UsageLedger;
- HotCache;
- CapabilityRegistry.

Infrastructure adapters may implement those interfaces:

- Postgres intelligence repository;
- SerpApi discovery adapter;
- browser verification adapter;
- future supplier adapters;
- future Redis hot-cache adapter;
- static-bearer or OAuth authentication adapters.

The domain layer must not require knowledge of Redis, SerpApi, ngrok, a specific
seller, a payment processor, or a specific OAuth vendor.

## One-Authority Map

| State | Authority |
| --- | --- |
| Discovery history | PostgreSQL |
| Current accepted discovery head | PostgreSQL |
| Intelligence revisions | PostgreSQL |
| Verified observations | PostgreSQL |
| Evidence fragments | PostgreSQL |
| Usage/billing ledger | PostgreSQL |
| Transaction intents and outcomes | PostgreSQL |
| Agent/client authorization result | Internal Principal produced by auth boundary |
| Redis/hot-cache result | Disposable copy only |
| Search-provider result | Input only |
| Browser/provider response | Evidence input only |
| MCP/REST response | Projection only |

If two systems can independently claim authority for the same state, the design
requires review before implementation.

## Capability-First Degraded Mode

The application should expose what it can currently do rather than collapse
optional-provider failure into a generic server failure.

Target capabilities include:

- cached_intelligence;
- live_discovery;
- verification;
- live_quote;
- purchase;
- order_tracking.

Example semantic response (illustrative, not a current API schema or availability claim):

```json
{
  "status": "partial",
  "degraded": true,
  "degraded_reasons": ["live_discovery_provider_unavailable"],
  "capabilities": {
    "cached_lookup": true,
    "refresh": false,
    "verify": true,
    "quote": false,
    "purchase": false
  }
}
```

This contract is especially important for AI agents, which should be able to
reason explicitly about the next permitted action.

## Liveness Versus Readiness

`/healthz` should mean the application process is alive.

A future `/readyz` or equivalent capability endpoint should report operational
capability state, for example:

- postgres available/unavailable;
- discovery available/degraded/unavailable;
- verification available/degraded/unavailable;
- transaction capability available/unavailable.

An optional provider outage must not cause an orchestrator to kill an otherwise
healthy application.

## Required Degraded Behavior

| Dependency unavailable | Must continue | Must stop/degrade |
| --- | --- | --- |
| Public ingress/ngrok | Local MCP/REST and local health | Remote reachability |
| Discovery provider | Policy-permitted cached intelligence and verified historical evidence | Fresh external discovery |
| Verification/browser provider | Discovery/cached intelligence and existing verified history | New verification |
| Future Redis | Fall through to PostgreSQL | Hot-cache acceleration only |
| Optional reasoning provider | Deterministic planning/structured procurement where supported | Optional semantic enrichment |
| Supplier API | Discovery, comparison, durable purchase intent | New execution through that supplier |
| Payment provider | Durable purchase intent and policy evaluation | Payment completion |
| External auth issuer | Locally verifiable existing sessions only where safe | New external authentication/refresh that requires issuer |
| PostgreSQL/Neon | Process liveness, request validation, non-authoritative deterministic parsing | Authoritative procurement results, durable mutation, transaction execution |

Continuing capabilities require their remaining dependencies, source-policy
permissions, and existing authorization. This table does not grant new authority
or permit historical evidence to be relabeled as freshly verified.

## Provider Failure Model

Provider state should be explicit and machine-readable:

- AVAILABLE;
- DEGRADED;
- RATE_LIMITED;
- UNAVAILABLE;
- MISCONFIGURED.

Repeated provider failure should enter bounded backoff/circuit-breaker behavior
rather than repeatedly spending quota. This target does not authorize automatic
retries or relax the current no-retry constraint.

Cache or provider failure must never silently authorize external work.

## Cache Architecture Rule

PostgreSQL owns semantic cache state.

A future Redis layer is permitted only as a disposable hot-cache accelerator.
Redis loss must fall through to PostgreSQL and preserve equivalent semantics.

Redis must not own:

- relevance/quarantine decisions;
- evidence authority;
- verified observations;
- accepted discovery-head identity;
- billing/usage authority;
- transaction authority.

Cache upgrades should prefer versioned identities and immutable history over
destructive deletion, retaining history only when source policy permits.

## Transaction Architecture Rule

Transactions require stronger isolation than search.

The target pattern is durable intent plus idempotent execution:

Agent -> purchase intent -> PostgreSQL transaction -> authorization + idempotency +
outbound action -> COMMIT -> provider executor -> immutable outcome.

Here, “outbound action” means a durable outbox record committed atomically with
the authorized intent and idempotency state. The external provider call occurs
only after COMMIT; it is not a network purchase call inside the database
transaction. Any future queue/worker transports or schedules this durable work
without becoming the authority for the intent or outcome.

If a supplier disappears after intent commit, the intent remains durable in an
explicit pending/provider-unavailable state.

External purchase calls must not be blindly retried unless the provider supports
an idempotency mechanism the system controls.

Finding, ranking, or recommending an option never grants authority to purchase it.

## Authentication Architecture Rule

External authentication mechanisms must resolve to one internal Principal model.

Target Principal dimensions:

- client/organization;
- agent identity;
- permissions;
- budget/limits;
- delegated authority;
- policy context.

Static bearer, OAuth, JWT, or enterprise identity are adapters. Procurement logic
should not change when the external authentication mechanism changes.

## Failure-Mode Testing Requirement

Every new adapter must ship with failure-mode tests before production use.

Minimum examples:

- discovery provider unavailable -> policy-permitted cached lookup still works, no external request counted, capability reports degraded;
- Redis unavailable -> PostgreSQL fallback returns equivalent semantic result;
- verifier unavailable -> DISCOVERED never becomes VERIFIED;
- supplier unavailable during purchase -> durable pending/failure state, no duplicate order;
- public ingress unavailable -> local service remains healthy;
- PostgreSQL unavailable -> no authoritative facts are fabricated and no transaction executes.

The zero-request discovery example is a known-unavailable provider with no
outbound request attempted. If an actual request is attempted and fails, it must
still be counted truthfully. UNKNOWN != ZERO remains unchanged.

## Architectural Red Lines

Do not:

- make Redis authoritative;
- make a provider response a verified fact without verification;
- hide external discovery behind a cache read;
- make public ingress part of business logic;
- couple procurement-domain code directly to vendor SDKs;
- allow transaction execution before durable intent/idempotency;
- add a second source of truth as an outage workaround;
- add infrastructure because it is fashionable rather than measured.
