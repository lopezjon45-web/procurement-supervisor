# Procurement Supervisor — current navigation

**AQ-010 Cache/Relevance Integrity** is the sole current Roadmap Stage 1 task.
Jon accepted/closed AQ-009 Stage 0 and approved only AQ-010 Slice 1A local
implementation, tests, control synchronization, and a sanitized Issue #1
handoff. Slice 1A is implemented locally and awaits supervisor/Jon review;
Slice 1B and migration 006 remain unapproved. See
[CURRENT_TASK.md](CURRENT_TASK.md), [APPROVAL_QUEUE.md](APPROVAL_QUEUE.md), and
[CODEX_REPORT.md](CODEX_REPORT.md) for the current scope and evidence. The
previous AQ-009 navigation below is historical after this decision.

---

## Prior AQ-009 navigation — historical

Public shared control plane for Jon, ChatGPT, and Codex. Jon is the final YES / NO
authority; ChatGPT is strategic supervisor and plan keeper; Codex executes only
the exact approved scope.

## Current position

**AQ-009 — Architecture Resilience Baseline** is the single current task,
advancing **Roadmap Stage 0**. Documentation preparation and publication are
approved: Jon replied **“yes”** to the prepared eight-file packet, authorizing
commit/push, one sanitized Issue #1 handoff, and verification. The next gate is
supervisor review. Cycle state: **APPROVAL_REQUIRED**.
No product implementation is authorized.

**AQ-008 is COMPLETED / SUPERVISOR-REVIEWED** per Jon's supplied handoff:
one independent outside phone-agent cache-only call; STALE with five DISCOVERED
leads; compatibility/freshness unknown. Reported Neon evidence: one tester row,
one search call, zero other tool calls, zero measured external discovery, zero
reservations/settlements. Individual-row `verification_fetches` remains
**NULL / not measured**, not independently measured zero. Feedback identified
understandable structure but stale, non-actionable and clearly irrelevant leads.
The earlier credential blocker is historical; details and attribution are in
[AQ-009_CONTROL_SYNC.md](AQ-009_CONTROL_SYNC.md).

## Read before each cycle

Read the existing governance/control sequence first:

1. [AI_SUPERVISOR.md](AI_SUPERVISOR.md) — binding governance and evidence invariants.
2. [DECISIONS.md](DECISIONS.md) — latest explicit direction and retained locked decisions.
3. [CURRENT_TASK.md](CURRENT_TASK.md) — the single current task and stop boundary.
4. [APPROVAL_QUEUE.md](APPROVAL_QUEUE.md) — exact decisions and pending approval gates.
5. [CODEX_REPORT.md](CODEX_REPORT.md) — work, evidence, limitations and outcome.

Then read the foundation and reconciliation documents:

- [ROADMAP.md](ROADMAP.md) — authoritative long-term navigation through stages 0–12.
- [ARCHITECTURE_RESILIENCE.md](ARCHITECTURE_RESILIENCE.md) — authority, dependencies, degraded behavior and failure requirements.
- [AQ-009_CONTROL_SYNC.md](AQ-009_CONTROL_SYNC.md) — supplied AQ-008 completion and AQ-009 scope/approval provenance.

Every task must identify its roadmap stage. Architecture targets are not claims
of implemented capability. After foundation review, cache/relevance hardening
is the first implementation direction; exact implementation and gated actions
still require separate approval.

Use the existing permanent
[Procurement Supervisor Queue Issue #1](https://github.com/lopezjon45-web/procurement-supervisor/issues/1)
for sanitized handoffs and decisions. Keep it open; do not create a replacement.
Earlier issue bodies/comments and the records below remain historical, not
current blockers or renewed approval.

## Unchanged boundaries

The permanent evidence rules and AI_SUPERVISOR.md remain unchanged. This cycle
authorizes no product/runtime/schema/dependency/auth/provider/source-policy
changes, production deployment, procurement MCP test calls, credential rotation,
transactions/payment/billing, or cache deletion/invalidation. Do not create or
apply migration 006.

Do not publish secrets, credentials, password-bearing database URLs, bearer
tokens, customer data, raw provider payloads, or private logs. Each cycle ends in
exactly one of CONTINUE, APPROVAL_REQUIRED, or BLOCKED as defined in the contract.

---

<!-- AQ009_HISTORICAL_RECORDS -->
## Historical records — preserved verbatim

Everything below is historical. Earlier headings, task IDs, stop states, and
approval restrictions describe their original cycles; they are not additional
current tasks or renewed execution authority. Only the current AQ-009 section
above governs this cycle. Standing evidence rules and unmodified approval gates
remain in force.

# AQ-008 — Approved; BLOCKED at tester credential prerequisite

Jon explicitly directed AQ-007 to be recorded as SUPERVISOR-REVIEWED and approved AQ-008 in the active instruction beginning “Jon explicitly approved AQ-008: one outside-agent consumption test.” This records his decisions without changing strategy or treating unverified leads as product evidence.

A separate Claude Code 2.1.236 client was found with an authenticated existing login. The securely entered bearer did not match the existing tester-1 registry entry. Execution stopped before temporary-container creation, public-routing changes, Claude inference, or any procurement call. No owner fallback, key rotation or repeat entry was attempted. The session bearer was cleared.

Cache status and lead count were not measured; no actual tester feedback exists. Calls, discovery attempts, provider account requests, destination fetches, crawling and verification were all zero. Owner remains consumed 3/held 0 (cap 10); tester-1 remains consumed 0/held 1 (cap 5). Ledger digests, tool counts and reservations/settlements were unchanged; no ordinary usage row was expected because no call occurred.

The reviewed AQ-007 image digest sha256:3d42bc32ebba29acbef470a27e26cab91c7697b5f7b59ebb61ef9ed873358818 remains preserved. Production and original staging retain their AQ-008 entry IDs, images, start times and configuration; browser OFF and SerpApi absent. The temporary AQ-008 container is absent. Production ngrok never moved from localhost:3000; one tunnel/process and local/public health were independently verified. Pre-existing production request inspection remains enabled; no authenticated traffic was sent through it. The setup-only inspection check was corrected without runtime changes before the actual credential prerequisite failed.

Safe validation: Python before/final each 666 passed / 0 failed / 46 skipped; MCP/HTTP 57 passed / 0 failed / 0 skipped with provider/database doubles and outbound network denial; four mocked one-call guard checks passed. No product code/schema/dependency/auth/policy/public-tool/rollout/Registry/cloud changes. These checks do not substitute for outside-agent consumption feedback.

Sanitized packet: https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5788351714

state: BLOCKED
task: AQ-008
next_action: Resolve secure local entry for the existing tester-1 bearer, then resume only the approved one-call cache-only scope. No further activity this cycle.

All prior task-status entries below are historical. AQ-007 is supervisor-reviewed; AQ-008 remains approved within its original scope, with execution blocked rather than permission expanded.

---

# AQ-007 — Completed; APPROVAL_REQUIRED

Jon explicitly approved this one controlled relevance regression in the active 2026-09-22 instruction. The approval covered the existing AQ-006 patch including the anchored-prefix correction, a separately tagged hardened temporary runtime, hidden owner-first credential entry, one public request/at most one external search, temporary exclusive ngrok routing, cleanup, and this sanitized supervisor publication/reconciliation. This records Jon's explicit decision; no further work is approved.

Request: replacement charger; device MacBook Air; model A2681; model_identifier omitted; minimum_evidence=discovered; both refresh flags true. Actual prioritized and persisted query: MacBook Air A2681 replacement charger. Result: one public call, one measured search attempt, miss → hit, success, five discovered/unverified leads, compatibility unknown. No retries, pagination, fallback, destination fetches, crawling, verification, or inferred product facts.

Comparable URL evidence versus AQ-005: three apparently topical retail search/category leads, one topical information guide, one indeterminate opaque catalog lead, zero visibly off-topic leads; AQ-005 had two apparently off-topic leads and three indeterminate video URLs. Both returned five. This suggests a better visible topical mix, not proven procurement usefulness or compatibility; changed query/filtering, time and upstream ranking prevent causal attribution.

Provider readings 242 → 241 are separate from one measured attempt; reserve 25 preserved. Owner consumed 2 → 3 of 10, held 0 → 0, exactly one reservation/settlement. Tester-1 consumed 0/held 1 and selected ledger digest unchanged. Credentials cleared, only temporary AQ-007 container removed, production routing restored to localhost:3000 and independently healthy. Both original containers/configurations/image tags and registry unchanged; browser OFF. Secret-free AQ-007 image retained: procurement-mcp:aq007-reviewed-20260922, sha256:3d42bc32ebba29acbef470a27e26cab91c7697b5f7b59ebb61ef9ed873358818.

Prerequisites and final Python: 666 passed / 0 failed / 46 skipped each run; MCP/HTTP prerequisites including remote-test.js: 57 passed / 0 failed / 0 skipped with external outbound networking OS-blocked and I/O doubles. All 37 packaged runtime files match reviewed source; protected baseline files, inherited hardening and anchored correction preserved. No product code, dependency, schema, auth, source-policy, public-tool, production-container or registry publication changes.

Sanitized packet: https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5788153252

state: APPROVAL_REQUIRED
task: AQ-007
next_action: Supervisor review only. No further search, deployment or roadmap step.

All status text below is historical; earlier AQ-006 pending and AQ-007 blocked/in-progress statuses are superseded only by this completed bounded cycle. Truth rules and limitations remain in force.

---

# Current supervisor status — 2026-09-21

AQ-004 is completed and reviewed. AQ-005 is explicitly approved by Jon for bounded owner-only candidate-quality measurement, up to three evidence-backed queries. See CURRENT_TASK.md and APPROVAL_QUEUE.md for the exact constraints. This update supersedes historical pending/not-approved status text below; it does not relax truth rules or authorize additional work.

---

# Procurement Supervisor

Public shared control plane for Jon, ChatGPT, and Codex.

## Roles

- **Jon:** final YES / NO approval authority.
- **ChatGPT:** strategic supervisor and plan keeper.
- **Codex:** implementation executor; works only within the active approved task.

## Control files

Read these in order before each work cycle:

1. [AI_SUPERVISOR.md](AI_SUPERVISOR.md) — binding governance.
2. [DECISIONS.md](DECISIONS.md) — locked direction and constraints.
3. [CURRENT_TASK.md](CURRENT_TASK.md) — the single active task.
4. [APPROVAL_QUEUE.md](APPROVAL_QUEUE.md) — explicit approval requests and decisions.
5. [CODEX_REPORT.md](CODEX_REPORT.md) — execution evidence, limitations, and outcome.

Use the permanent **Procurement Supervisor Queue** issue for handoffs, review,
and Jon's decisions. Keep it open across tasks. Link approvals to the applicable
queue item; silence and recommendations are not approval.

Every work cycle ends with exactly one outcome: `CONTINUE`,
`APPROVAL_REQUIRED`, or `BLOCKED`. Definitions are in AI_SUPERVISOR.md.

## Current position

Active task: `SERPAPI-FREE-TIER-GUARDRAIL-001`.
Local guardrail implementation was reported complete; review is pending.
AQ-001 remains PENDING. Real credentials and live discovery are not authorized.
This setup creates governance documents only and starts no implementation.

## Public repository safety

Never publish secrets, credentials, database URLs containing passwords, bearer
tokens, customer data, or private logs in files, issues, comments, commits, or
attachments. Publish only sanitized summaries and test counts. Keep product
runtime code and private operational material outside this control repository.
