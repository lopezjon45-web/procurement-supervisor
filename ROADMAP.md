# Procurement Intelligence Roadmap

## Document status and authority

This is the authoritative long-term navigation map for the project. It was
established under AQ-009, whose Stage 0 foundation is accepted and closed. It is
a target sequence, not a claim of implemented capabilities or an authorization
to execute any stage. Jon remains the final YES / NO authority under
[AI_SUPERVISOR.md](AI_SUPERVISOR.md); the single active task and its gates are
recorded in [CURRENT_TASK.md](CURRENT_TASK.md) and
[APPROVAL_QUEUE.md](APPROVAL_QUEUE.md).

## North Star

Build the default procurement interface for AI agents: one obvious entry point
that can understand a procurement need, discover options, screen relevance,
verify evidence and compatibility, prepare or execute transactions under explicit
authority, track outcomes, and preserve provenance, freshness, cost, policy, and
uncertainty.

The product is not generic search. It is procurement infrastructure for agents.

## Permanent Product Invariants

- DISCOVERED != VERIFIED.
- SEARCH SNIPPET != PRODUCT FACT.
- STALE != CURRENT.
- MODEL MENTION != COMPATIBLE.
- UNKNOWN != NO.
- UNKNOWN != ZERO.
- AUTHENTICATED != AUTHORIZED.
- Finding an item never grants authority to buy it.
- A cache read never silently authorizes external discovery.
- External providers may supply data or transport requests, but they do not own procurement truth.
- Historical evidence is preserved immutably when policy permits.
- Every externally visible capability must degrade explicitly rather than fabricate a result.
- Every task must identify which roadmap stage it advances.

## Cross-Cutting Gates

These apply across stages. Both are approved as permanent direction; neither is
approved for installation or implementation. Full requirements are in
[DECISIONS.md](DECISIONS.md).

### Universal Agent Governance Harness

- Governance is vendor-neutral; canonical truth lives in versioned files.
- No hidden model memory is required.
- Every agent bootstraps from [START_HERE.md](START_HERE.md).
- Vendor-specific agent files are adapters, never authority.
- Deterministic guard scripts supplement prose rules.
- Installation (adapters, guard scripts, vendor files) is separately
  approval-gated.

### Secure Agent Handshake

- Mandatory before broad public agent access, regardless of which stage is
  current. Static bearer authentication remains a bounded pilot mechanism only.
- The full identity and delegated-authority model belongs to Stage 8; the
  minimum handshake gate does not wait for Stage 8.
- AUTHENTICATED != AUTHORIZED.
- Design and implementation are separately approval-gated.

## Roadmap Sequence

### Stage 0 — Architecture Resilience Baseline

Goal: establish the dependency and authority model before adding more services.

Deliverables:

- authoritative-state map;
- dependency tiers;
- ports/adapters boundaries;
- capability/degraded-mode contract;
- liveness versus readiness semantics;
- provider-failure model;
- transaction idempotency/outbox principles;
- Redis-as-disposable-accelerator rule;
- failure-mode testing requirements.

Exit condition: a written, reviewed foundation defines how the system behaves
when each optional dependency disappears.

Status: **ACCEPTED / CLOSED** (AQ-009). See
[ARCHITECTURE_RESILIENCE.md](ARCHITECTURE_RESILIENCE.md).

### Stage 1 — Cache and Relevance Integrity

Goal: cached data must never become authoritative merely because it is cached.

Target behavior:

- richer cache states such as fresh, stale-servable, hard-stale, negative-backoff, refresh-in-progress, and quarantined;
- deterministic relevance admission before head promotion;
- planner/relevance/cache versioning;
- last-known-good fallback where policy permits;
- negative caching for bounded transient failure classes;
- cross-process refresh single-flight before external quota is spent;
- no destructive historical-cache clearing as the normal upgrade path.

Exit condition: a bad discovery batch cannot replace a known-good active head,
and stale/negative states are explicit.

Status: **CURRENT** (AQ-010).

- Slice 1A: COMPLETED / SUPERVISOR-REVIEWED.
- Slice 1B: design and supervisor review only; implementation NOT APPROVED.
- Migration 006: creation and application NOT APPROVED.

Open risks:

1. Real PostgreSQL integration and concurrency remain unvalidated.
2. Repeated refresh after quarantine may spend quota until Slice 1B
   coordination/backoff is implemented and validated.
3. Broad relevance improvement is unproven; measured live evidence is very
   narrow (one repeated query).

Before Slice 1B can be ACCEPTED / CLOSED:

- PostgreSQL integration and concurrency are exercised on an isolated,
  throwaway database under separately approved scope;
- quarantine and refresh backoff behavior is validated;
- refresh coordination / fencing behavior is validated.

Before Stage 1 can be declared COMPLETE:

- a small, fixed, predeclared multi-query relevance regression set based on
  real procurement demand is run under separately approved scope;
- results are reported without claiming causation or quality beyond the sample.

### Stage 2 — Agent-Facing Procurement Contract

Goal: make the service obvious and efficient for AI agents.

Primary front door target: `find_procurement_options`.

The agent should not need to understand internal pipeline tools. Responses should expose:

- request interpretation;
- structured options;
- provenance;
- evidence state;
- compatibility state;
- freshness;
- explicit unknowns;
- available next actions;
- current capabilities such as refresh, verify, quote, and purchase.

Exit condition: an independent agent can consume one stable procurement contract
without orchestrating internal tools. This target does not rename or replace any
existing MCP tool until a separately approved Stage 2 task does so.

### Stage 3 — Procurement Intelligence Quality

Goal: make returned options actionable, not merely structurally valid.

Focus:

- product/part identity;
- manufacturer, SKU, MPN, GTIN when known;
- price, stock, seller, shipping, estimated delivery when known;
- source-aware discovery metadata clearly separated from verified product facts;
- duplicate/product resolution across sellers and sources;
- ranking based on evidence and procurement usefulness rather than raw search rank.

Exit condition: returned options are materially useful without weakening evidence rules.

### Stage 4 — Compatibility Intelligence

Goal: make “will this work?” a first-class, evidence-backed capability.

Model:

- product/part compatible with device/model;
- supersedes/equivalent-to relationships;
- required components;
- supported, unsupported, conflicting, or unknown status;
- exact evidence references for compatibility assertions.

Exit condition: compatibility conclusions are machine-readable and traceable to evidence.

### Stage 5 — Transaction Readiness

Goal: prepare the system to transact without coupling discovery to authority.

Pipeline:

procurement option -> live quote -> eligibility -> client policy -> budget ->
authorization -> purchase intent -> idempotency gate -> provider execution -> order record.

Permanent rule: discovery or recommendation never grants purchase authority.

Exit condition: transaction state and authorization can be represented durably
before any purchase adapter is enabled.

### Stage 6 — Transaction Primitives

Target primitives:

- `request_quote`;
- `get_transaction_terms`;
- `create_purchase_intent`;
- `authorize_purchase`;
- `execute_purchase`;
- `get_order_status`;
- `cancel_order`;
- `request_return`.

Requirements:

- idempotency keys;
- immutable audit history;
- quoted versus charged totals;
- tax/shipping/currency;
- quote expiration;
- seller/order identity;
- authorization identity;
- exact agent/client identity;
- retry/failure semantics.

Exit condition: a repeated agent request cannot accidentally create duplicate orders.

### Stage 7 — Supplier Transaction Adapters

Goal: keep vendor-specific APIs outside the procurement core.

Core vocabulary:

- quote;
- reserve;
- purchase;
- cancel;
- track;
- return.

Provider-specific behavior remains behind replaceable adapters.

Exit condition: replacing one supplier integration does not require rewriting procurement logic.

### Stage 8 — Agent Identity and Delegated Authority

Goal: support safe autonomous procurement.

Long-term principal model:

- client/organization;
- agent identity;
- permissions;
- budget;
- purchase limits;
- seller restrictions;
- human-confirmation requirements;
- delegated authority.

Authentication mechanisms such as static bearer, OAuth, JWT, or enterprise
identity must resolve to the same internal Principal abstraction.

The Secure Agent Handshake requirements in [DECISIONS.md](DECISIONS.md) are the
minimum gate for broad public agent access and apply before this stage if broad
access is requested earlier.

Exit condition: authorization policy is independent of the external authentication mechanism.

### Stage 9 — Commercial Model

Goal: meter useful work rather than treating all calls equally.

Potential units:

- cached intelligence lookup;
- external discovery;
- verification fetch;
- compatibility resolution;
- live quote;
- transaction execution;
- premium-source access.

Exit condition: measured units map cleanly to customer value and provider cost.

### Stage 10 — Reliability and Scaling

Add infrastructure only after measured need.

Candidates:

- Redis hot cache;
- queue/workers;
- background cache warmers;
- regional replicas;
- CDN;
- expanded observability.

Rule: these components accelerate or schedule work; they do not become
authoritative procurement state.

Exit condition: removing an accelerator changes performance, not truth.

### Stage 11 — Proactive Procurement

Goal: move from reactive lookup toward lifecycle intelligence.

Examples:

- price opportunity detection;
- replenishment forecasts;
- stock-out alternatives;
- superseded part detection;
- compatibility-preserving substitutes.

Exit condition: agents can ask the platform to manage a procurement objective,
not only search once.

### Stage 12 — Agent-Native Procurement Platform

Target experience:

An agent can express a goal such as:

> I need a compatible replacement charger for this MacBook, delivered by Friday,
> under $75. Only purchase if compatibility is verified.

The platform can then understand, discover, screen, verify, compare, quote,
enforce constraints, request or consume authority, transact, track, and report
while preserving evidence and uncertainty.

## Dependency Policy

New external runtime services are not roadmap progress by themselves.

Before adding one, document:

- purpose;
- why the current application/Postgres architecture cannot reasonably provide the capability;
- authoritative state, if any;
- failure behavior;
- replacement path;
- cost;
- security impact;
- operational burden;
- rollback plan.

If the proposed service would own procurement truth or make optional-service loss
corrupt authoritative state, do not add it without an explicit architecture decision.
The dependency tiers and stricter measured-need rule are defined in
[ARCHITECTURE_RESILIENCE.md](ARCHITECTURE_RESILIENCE.md).

## Current Navigation

- Stage 0 — Architecture Resilience Baseline: **accepted / closed** (AQ-009).
- Stage 1 — Cache and Relevance Integrity: **current** (AQ-010).
  - Slice 1A: completed / supervisor-reviewed.
  - Slice 1B: design and review only; implementation not approved.
  - Migration 006: not approved.
- Stages 2–12: not started; no authorization exists for any of them.

New dependencies, production deployment, authentication changes, provider
activation, and transaction implementation each require their own approval.
