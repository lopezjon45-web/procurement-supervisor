# Current cross-cutting requirements — 2026-10-03

Jon approved the following directions for the control plane. They are required
future gates, not authorization to implement them or to advance the active task.

## Universal Agent Governance Harness

Canonical project governance must be vendor-neutral. Project truth must be
recoverable from plain, versioned repository files and recorded supervisor
state, with no hidden model memory required. Any unknown or future agent must
be able to begin from a universal `START_HERE.md`-style bootstrap. Vendor-specific
files such as `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, and Cursor rules are adapters
only; they are not authoritative.

Capability and authorization are separate checks. Missing, stale,
inconsistent, or unverifiable authority fails closed. Deterministic preflight
and guard scripts should supplement prose instructions. After every completed
gate, reconcile the supervisor repository without rewriting history, then
verify the remote commit SHA, exact changed files, and remote file contents
before advancing.

Installing this harness remains **APPROVAL_REQUIRED**. It requires its own
reviewed merge/collision plan and explicit Jon approval. This direction does
not authorize product-repository changes, skills or adapters, runtime code,
authentication, credentials, dependencies, or deployment.

## Secure Agent Handshake

Secure Agent Handshake is a mandatory security gate before broad public agent
access. Its future design must use TLS-protected transport; asymmetric proof
of key possession or an equivalently strong standard proof-of-possession
mechanism; a server-generated nonce/challenge with short expiration and
single-use replay protection; protocol/security-version binding and downgrade
resistance; short-lived sessions, sender-bound/proof-of-possession sessions
where practical, revocation and key rotation; and safe handshake audit records.
Authentication and authorization remain strictly separate:

**AUTHENTICATED != AUTHORIZED**

The external handshake must never expose or transmit long-lived private keys,
master credentials, database credentials, provider/API credentials, internal
refresh-fencing capabilities, or internal owner capability/token material.
Different agent ecosystems may use different authentication adapters, but
every successful method must resolve to the same internal Principal and
authorization boundary. Static bearer authentication may remain a bounded
pilot mechanism; it is not the intended long-term broad-public trust model.
Handshake design and implementation, including auth, key, and deployment
changes, remain separately **APPROVAL_REQUIRED**. No handshake code is
authorized by this entry.

## Active roadmap boundary

AQ-010 remains the sole active Roadmap Stage 1 task. Slice 1A is COMPLETED /
SUPERVISOR-REVIEWED. Corrected Python validation remains 682 passed / 0 failed /
46 skipped; full safe Node validation remains 57 passed / 0 failed / 0 skipped.
Real PostgreSQL integration/concurrency remains unvalidated. Slice 1B
implementation and migration 006 creation/application remain NOT APPROVED;
their existing design/review boundaries are unchanged.

---

## Historical roadmap — preserved verbatim

# Procurement Intelligence Roadmap

## Document status and authority

AQ-009 establishes this authoritative long-term navigation map in the control
plane. It is a target sequence, not a claim of implemented capabilities or an
authorization to execute later stages. Jon remains the final YES / NO authority
under [AI_SUPERVISOR.md](AI_SUPERVISOR.md); the single approved task and gates are
recorded in [CURRENT_TASK.md](CURRENT_TASK.md) and
[APPROVAL_QUEUE.md](APPROVAL_QUEUE.md). Foundation review is pending.

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
- Finding an item never grants authority to buy it.
- A cache read never silently authorizes external discovery.
- External providers may supply data or transport requests, but they do not own procurement truth.
- Historical evidence is preserved immutably when policy permits.
- Every externally visible capability must degrade explicitly rather than fabricate a result.
- Every task must identify which roadmap stage it advances.

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
existing MCP tool in AQ-009.

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

**AQ-009 Architecture Resilience Baseline — Stage 0 is accepted and closed.**
**AQ-010 Cache/Relevance Integrity — Stage 1 is current.** Jon approved only
Slice 1A local implementation and tests under the bounds in CURRENT_TASK.md.
Slice 1A is locally complete and awaits review; Slice 1B and migration 006
remain separate gates. New dependencies, production
deployment, authentication changes, provider activation, and transaction
implementation are not authorized by this Stage 1A decision.
