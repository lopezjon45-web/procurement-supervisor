# Current decisions — AQ-010 / Stage 1

Jon's active instruction beginning “YES — I approve AQ-010 Slice 1A
implementation and tests” accepts and closes AQ-009 Stage 0. AQ-010 is the sole
current Roadmap Stage 1 task. Slice 1A implementation, tests, documentation,
control reconciliation, and the sanitized supervisor handoff are approved within
the exact bounds in CURRENT_TASK.md and APPROVAL_QUEUE.md. No durable
session-message URL was supplied. Jon remains the final YES / NO authority.

Cache admission is a lead-selection heuristic, never source permission or a
verified product, seller, price, stock, identity, or compatibility claim.
Preserve original URLs/timestamps, SourcePolicy limits, unknowns, budget guardrails,
one-query/20-row/five-lead bounds, and no automatic retry. Slice 1B and migration
006 require separate review/approval. Earlier AQ-009 directions below are
historical after Jon's acceptance; permanent evidence rules remain active.

---

# Current decisions — AQ-009 / 2026-09-28

## Authority and decision source

Jon remains the final YES / NO authority; ChatGPT remains strategic supervisor
and plan keeper; Codex remains implementation executor. AI_SUPERVISOR.md and its
permanent evidence rules are unchanged.

Source: Jon's active instruction titled “Codex Execution Prompt — AQ-009
Architecture Resilience Baseline” and the three documents supplied with it,
recorded in [AQ-009_CONTROL_SYNC.md](AQ-009_CONTROL_SYNC.md). No durable
session-message URL was supplied. This entry records Jon's explicit direction;
it does not infer approval.

## AQ-008 — COMPLETED / SUPERVISOR-REVIEWED

The earlier credential-prerequisite blocker was subsequently resolved through a
tester credential rotation under Jon's explicit approval, with owner identity
and other configuration preserved. The completed test used independent outside
phone-agent consumption: one cache-only `search_procurement_intelligence` call,
STALE, five DISCOVERED leads, unknown compatibility/freshness. Reported Neon
evidence confirms one tester row, one search call, zero other tool calls, zero
measured external discovery, zero discovery-budget reservations and settlements.
The individual usage row's `verification_fetches` is **NULL / not measured**,
never independently measured zero.

Outside-agent feedback: understandable response structure, but stale leads were
not actionable and included clearly irrelevant sources. Discovery relevance and
cache quality are the demonstrated gap. Completion/review does not verify leads
or establish procurement usefulness. Detailed scope and evidence limitations are
preserved in AQ-009_CONTROL_SYNC.md. No new rotation or test is authorized.

## AQ-009 — documentation publication approved; foundation review pending

AQ-009 is the single current task and advances Stage 0 of
[ROADMAP.md](ROADMAP.md), the authoritative long-term navigation map. Jon approved
establishing [ARCHITECTURE_RESILIENCE.md](ARCHITECTURE_RESILIENCE.md) in the control
plane. Its rules preserve:

- application/core plus PostgreSQL as the authoritative spine, with one authority per state;
- dependency tiers and measured need before new external runtime services;
- domain-facing ports with replaceable vendor adapters;
- explicit capability degradation and liveness separate from readiness;
- Redis as a disposable accelerator; PostgreSQL owns semantic cache state;
- durable authorized transaction intent, idempotency and atomic outbox before provider execution;
- one internal Principal abstraction and mandatory adapter failure-mode tests.

The roadmap elaborates the earlier pilot sequence without reopening consumed
approvals: preserve guardrails and pilot limits, address the evidence-backed
cache/relevance gap after foundation review, and defer broad publication until
value is proven. The laptop-hosted pilot remains the operating direction; cloud
migration is not approved. Stage 2's `find_procurement_options` is a future
target, not a current tool rename.

Standing constraints remain: max_queries=1 in the active intelligence discovery
path; no automatic retries; cache-first behavior; truthful
external_discovery_requests_attempted; approximately 25-search provider reserve;
owner=10 and tester-1=5 lifetime pilot caps; browser crawling OFF in production;
no new SerpApi credential activation.

## Exact approval gates

Preparation of these documents is approved. Jon subsequently replied **“yes”**
to the eight-file review packet and proposed commit message in the active
session, satisfying the separate commit/push gate. No durable message URL is
available. This YES authorizes only the reviewed documentation publication,
one sanitized handoff in permanent Issue #1, and commit/file verification.
Stop APPROVAL_REQUIRED for supervisor review afterward; review remains pending.

No product/runtime/schema/dependency/auth/provider/source-policy changes,
production deployment, procurement MCP test calls, credential rotation,
transaction/payment/billing implementation, or cache deletion/invalidation are
approved. Migration 006 may not be created or applied.

After foundation review, Stage 1 cache/relevance hardening is the first
implementation direction; review/publication does not itself authorize that
implementation. Jon must approve its exact scope and any gated actions.

---

<!-- AQ009_HISTORICAL_RECORDS -->
## Historical records — preserved verbatim

Everything below is historical. Earlier headings, task IDs, stop states, and
approval restrictions describe their original cycles; they are not additional
current tasks or renewed execution authority. Only the current AQ-009 section
above governs this cycle. Standing evidence rules and unmodified approval gates
remain in force.

# Current approved status — 2026-09-21

AQ-004 is COMPLETED AND REVIEWED, as explicitly directed by Jon on 2026-09-21 in the active Codex session. Its single public test recorded one external search attempt and five discovered/unverified leads, all compatibility unknown. Account readings were 244 before and after; observed delta zero is not a billing/cache determination. Owner durable usage became 1/10; tester history was unchanged. Credentials were cleared, the temporary container removed, and production tunnel/health restored without changing the production container/image. Result: https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5753722005 . This reviewed status does not establish candidate compatibility or broad procurement usefulness.

AQ-005 is EXPLICITLY APPROVED BY JON ON 2026-09-21. Decision source: Jon's instruction beginning “AQ-005 is explicitly approved by Jon on 2026-09-21” in the active Codex session. This records Jon's decision, not an approval inferred by Codex. This documentation-only sync precedes AQ-005 execution.

The AQ-004 not-approved and runtime-credential restrictions in the historical status below are superseded only within the explicit AQ-005 temporary-runtime scope in CURRENT_TASK.md and APPROVAL_QUEUE.md. Locked truth rules, operating direction, lifetime caps, and approval gates remain in force. No broader discovery, production change, verification, cloud, or registry authorization is implied.

---

# Locked Decisions

## Roles

Jon = final YES / NO approval authority.
ChatGPT = strategic supervisor and plan keeper.
Codex = implementation executor.

## Product and operating direction

Build universal procurement intelligence with explicit evidence and unknowns. Discovery leads are not verified product facts. Compatibility needs evidence. The laptop-hosted pilot remains the operating direction; cloud migration and broad publication require approval and demonstrated value.

## Locked sequence

1. SerpApi free-tier quota guardrails — completed and reviewed.
2. Enable one-search default discovery — existing behavior preserved.
3. Verify real candidate quality — AQ-001's one approved live test completed; broad usefulness is not yet proven.
4. Add per-client discovery quotas — implemented and reviewed under AQ-002.
5. Measure usage and free-tier consumption — AQ-003 measured provider-free runtime behavior; no new provider search was authorized.
6. Improve only gaps shown by tester evidence.
7. Publish broadly only after value is proven.

## Current constraints

- Preserve `max_queries=1` in the active intelligence discovery path.
- Preserve no automatic retries, cache-first behavior, and truthful `external_discovery_requests_attempted` accounting.
- Retain the approximately 25-search provider reserve.
- Keep SerpApi credentials absent from the laptop runtime until a new approval.
- Keep browser crawling OFF in production.
- Owner=10 and tester-1=5 are lifetime pilot caps, not periodic resets.
- No schema/migration, dependency, auth/authz, source-policy, production, registry, billing, or cloud changes without a new explicit approval.
- AQ-004 is not approved.

## Approval state

AQ-001's single live-search authorization was consumed. AQ-002 implementation and tests were completed. AQ-003 deployment and provider-free Neon-backed validation were completed within scope and await supervisor review. No approval is inferred for the next roadmap step.

## Work-cycle outcome

Each cycle must end in exactly one of CONTINUE, APPROVAL_REQUIRED, or BLOCKED, with the meaning defined in AI_SUPERVISOR.md.


## AQ-007 — explicit approval and completed bounded execution, 2026-09-22

Decision source: Jon's active instruction beginning “Jon explicitly approved AQ-007: one controlled live relevance regression.” No session-message URL is available. Scope: existing AQ-006 patch including anchored-prefix correction; one owner-authenticated public replacement-charger request with MacBook Air/A2681, omitted model identifier, discovered minimum and both refresh flags true; at most one search; cache-first, max_queries=1, no retries or destination fetch/verification; hidden session credentials, temporary hardened image/container and exclusive tunnel, then cleanup and production restore. This records the explicit approval without changing strategic decisions.

The single authorized call completed with one measured search attempt and five unverified leads; owner usage 2 → 3, tester unchanged, reserve preserved, production restored. AQ-007 is execution-complete and APPROVAL_REQUIRED for review. The prior AQ-006 live-review request was authorized only through AQ-007; earlier AQ-007 credential-blocked/preparation status is historical. No ongoing search or production rollout authorization exists. Packet: https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5788153252


## AQ-007 supervisor-reviewed; AQ-008 approved and credential-blocked

Decision source: Jon's active instruction beginning “Jon explicitly approved AQ-008: one outside-agent consumption test,” including “Record AQ-007 as supervisor-reviewed and AQ-008 as approved.” No durable session-message URL is available. AQ-007 is SUPERVISOR-REVIEWED; that review does not verify its leads.

AQ-008 authorizes one existing outside tester-1 agent/client to consume the reviewed AQ-007 image's cache-only response for replacement charger, device MacBook Air, model A2681, omitted model identifier, minimum_evidence discovered, both refresh flags false. Preserve hidden tester credential entry, unchanged registry/database/auth/hardening, browser OFF, SerpApi absent, temporary exclusive routing and cleanup. No owner fallback, provider/destination requests, refresh, additional procurement calls or invented feedback. Publication/reconciliation is authorized; strategy and all remaining gates are unchanged.

Execution stopped because hidden tester-1 entry did not match the unchanged registry. No call, feedback, new usage, temporary runtime, or routing swap occurred; production health and unchanged budgets were verified. Status BLOCKED. Matching existing tester-1 secure entry is the unresolved prerequisite; no rotation or expanded scope is approved. Packet: https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5788351714
