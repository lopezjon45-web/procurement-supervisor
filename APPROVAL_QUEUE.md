# Current approval queue — AQ-010

Only Jon can decide YES / NO. Pending means no execution authorization.

## AQ-009 — Stage 0 ACCEPTED / CLOSED

Jon accepted and closed AQ-009 Stage 0 in the active instruction beginning
“YES — I approve AQ-010 Slice 1A implementation and tests.” The published
architecture remains the foundation; its historical publication and review
records below are preserved, not current blockers.

## AQ-010 — Stage 1 Slice 1A APPROVED BY JON

The same explicit instruction approves control-plane synchronization and
bounded local Slice 1A implementation/tests: relevance admission before head
promotion; retail route handling and synthetic AQ-005/AQ-007 regressions;
planner/relevance/request-cache v3; fresh, stale-servable, hard-stale,
quarantined states; 24-hour fresh plus at most 24-hour stale-servable subject to
stricter SourcePolicy; same-version last-known-good; additive safe diagnostics;
and necessary documentation. Existing tool names, public inputs, legacy
status/cache-status values, exact URLs, provenance, and evidence boundaries stay.
Use mocked provider data and deny external networking.

Slice 1B, migration 006 or other DDL, cross-process refresh ownership, bridge
coordination, new dependencies, provider/account requests, live MCP calls,
production/deployment, auth/credentials, SourcePolicy changes, destructive
cache work, and transaction/payment work are NOT APPROVED. Stop if 1A requires
any such expansion. Publish one sanitized handoff after tests, then stop
APPROVAL_REQUIRED for supervisor/Jon review before 1B or migration 006.

Slice 1A local implementation and safe tests are complete; review is now
**PENDING**. Completion does not approve deployment, Slice 1B, or migration 006.

---

## AQ-009 prior queue record — historical

Only Jon can decide YES / NO. Pending means no execution authorization.

## AQ-008 — COMPLETED / SUPERVISOR-REVIEWED

Recorded from Jon's supplied [AQ-009_CONTROL_SYNC.md](AQ-009_CONTROL_SYNC.md):
the tester credential was subsequently rotated under explicit approval, and an
independent phone agent completed one cache-only consumption call. STALE, five
DISCOVERED leads, unknown compatibility/freshness. Reported Neon evidence:
one tester row, one search call, zero other tools, zero measured external
discovery, zero reservations/settlements. Individual-row `verification_fetches`
was **NULL / not measured**, not independently measured zero. Feedback exposed
irrelevant, stale, non-actionable leads despite understandable structure.

The earlier blocked attempt is retained below as history. Its no-rotation
restriction described that attempt; the later rotation is recorded as completed
under Jon's supplied approval, not performed or newly authorized here.

## AQ-009 — Architecture Resilience Baseline / Stage 0

- Documentation/control-plane preparation: **APPROVED BY JON** in the active
  instruction titled “Codex Execution Prompt — AQ-009 Architecture Resilience
  Baseline”; source recorded in AQ-009_CONTROL_SYNC.md; no durable session-message
  URL supplied.
- Commit/push and the subsequent sanitized Issue #1 handoff: **APPROVED BY JON**
  through his explicit **“yes”** to the prepared eight-file review packet and
  proposed commit message in this active session; no durable message URL supplied.
- Foundation/supervisor review: **PENDING**, after publication.
- Product implementation: **NOT AUTHORIZED** by preparation, publication, or this entry.

### Concrete publication request

Add ROADMAP.md, ARCHITECTURE_RESILIENCE.md, and AQ-009_CONTROL_SYNC.md. Update
CURRENT_TASK.md, DECISIONS.md, APPROVAL_QUEUE.md, CODEX_REPORT.md, and README.md.
Keep AI_SUPERVISOR.md and all historical text unchanged.

Approved commit message: `docs: reconcile AQ-008 and establish AQ-009 resilience baseline`.

Jon's YES authorizes committing/pushing this exact documentation scope, posting one sanitized
handoff to the existing permanent
[Supervisor Queue Issue #1](https://github.com/lopezjon45-web/procurement-supervisor/issues/1),
and verifying the resulting commit/files. Stop APPROVAL_REQUIRED for supervisor review.

Why approval is required: Jon explicitly instructed “STOP for my YES before
committing or pushing anything.” The agreed workflow and mandatory gates in
AI_SUPERVISOR.md also require staying within the exact approved publication scope.

Risk/cost: public documentation publication only; no procurement/provider quota,
runtime action, or data mutation. Use sanitized summaries; no secrets or private
logs. Alternative: retain the local draft pending review. Rollback: an explicitly
approved follow-up documentation correction/revert preserving Git history, with
no product/data rollback.

Jon publication decision: **YES**, recorded from his reply to the prepared
publication packet. The final commit and remote-file verification evidence will
be recorded in the one approved Issue #1 handoff. This decision does not approve
the foundation review outcome or any product implementation.

### Excluded actions

No product code, migration 006 or any schema/migration creation/application,
dependencies/Redis, auth/authz, credentials/rotation, providers/SerpApi/discovery,
procurement MCP test calls, source policy, production containers/deployment,
transactions/payment/billing, or cache deletion/invalidation.

Next gate after publication: supervisor review of the foundation. Cache/relevance
hardening is the first later implementation stage and requires separately scoped
approval. No AQ-010 or other concurrent task is opened.

state: APPROVAL_REQUIRED
task: AQ-009
next_action: Supervisor review of the published AQ-009 foundation before any implementation.

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

# AQ-008 — Approved; outside-agent prerequisite check

Jon explicitly approved AQ-008 in the active instruction beginning “Jon explicitly approved AQ-008: one outside-agent consumption test.” He directed AQ-007 to be recorded as supervisor-reviewed. Decision source is this active instruction; no durable session-message URL is available. AQ-007 is now SUPERVISOR-REVIEWED, without promoting its leads or establishing purchase suitability. AQ-008 is APPROVED, with execution conditional on a separate existing tester agent/client being available. Codex or a Codex subagent calling the tool does not qualify.

Exact scope: reuse the verified AQ-007 image digest sha256:3d42bc32ebba29acbef470a27e26cab91c7697b5f7b59ebb61ef9ed873358818 in a temporary hardened AQ-008 container, unchanged registry/database/auth, browser OFF and SERPAPI_API_KEY absent. Existing tester-1 bearer through secure local entry only; no owner fallback. Confirm the separate tester before public routing changes. One tester search_procurement_intelligence call: query replacement charger, device MacBook Air, model A2681, model_identifier omitted, minimum_evidence discovered, both refresh flags false. Report stale honestly; stop on missing cache without refresh. No provider/account requests, destination fetch, crawling, verification or additional procurement-tool calls.

Capture actual tester feedback on useful next steps, missing purchase facts, clarity of discovery/freshness/compatibility, and reuse intent. Feedback is not verified product evidence. Confirm zero attempts and unchanged consumed/held budgets; ordinary zero-attempt usage logging is expected. Clear bearer, remove only temporary AQ-008 container, restore production localhost:3000 and independently verify health even on failure. Preserve original containers/images. Publish one sanitized packet and reconcile controls; no code/schema/dependency/auth/policy/public-tool/production-rollout/Registry/cloud changes. End APPROVAL_REQUIRED or BLOCKED.

state: CONTINUE
task: AQ-008
next_action: Confirm a separate tester agent/client is available before creating a public test route.

All earlier status entries below are historical and superseded by this explicit approval/review record within its bounded scope.

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

# Current approval update — 2026-09-21

AQ-004 is COMPLETED AND REVIEWED, as explicitly directed by Jon on 2026-09-21 in the active Codex session. Its single public test recorded one external search attempt and five discovered/unverified leads, all compatibility unknown. Account readings were 244 before and after; observed delta zero is not a billing/cache determination. Owner durable usage became 1/10; tester history was unchanged. Credentials were cleared, the temporary container removed, and production tunnel/health restored without changing the production container/image. Result: https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5753722005 . This reviewed status does not establish candidate compatibility or broad procurement usefulness.

## AQ-005 — Approved bounded candidate-quality measurement

AQ-005 is EXPLICITLY APPROVED BY JON ON 2026-09-21. Decision source: Jon's instruction beginning “AQ-005 is explicitly approved by Jon on 2026-09-21” in the active Codex session. This records Jon's decision, not an approval inferred by Codex. This documentation-only sync precedes AQ-005 execution.

Owner client only; baseline usage 1/10. Tester-1 must remain untouched. Select up to three distinct real procurement queries from existing tester-demand evidence, excluding AQ-004's rear-wiper query. Do not invent demand or pad the sample: use fewer when fewer suitable uncached queries exist. Each selected query gets at most one public MCP discovery call with refresh_if_missing=true, refresh_if_stale=true, minimum_evidence=discovered, and max_queries=1 per provider request. Cache hits consume zero and must be reported without repeating the query. No retries, second search per query, crawling, destination fetches, verification, or compatibility promotion.

Use a temporary staging-only container from the existing pinned hardened staging image. Preserve UID 10001, read-only filesystem, dropped capabilities, no-new-privileges, tmpfs restrictions, memory/CPU/PID limits, loopback binding, unchanged Neon configuration and client registry, and browser crawling OFF. Production container/image remain unchanged. Hidden local entry and inherited runtime environment only for SERPAPI_API_KEY; never print or put the value in chat, arguments, files, images, or logs. Temporarily expose only staging through ngrok, without pooling or host-header override. Clear the key, remove only the temporary AQ-005 container, restore ngrok to localhost:3000, and verify production health and endpoint identity.

Report each query's cache state, actual external attempts, lead count, source-type/relevance observations, and explicit unknowns without compatibility claims. Keep provider account readings separate from measured attempts; preserve the 25-search reserve as far as actual attempts allow. Verify no usage double-counting. Publish one sanitized AQ-005 packet to Supervisor Issue #1, then stop for review.

The historical AQ-004 not-approved entry below is superseded by the explicit decisions above. Earlier approvals do not grant continuing search authorization.

---

# Approval Queue

Only Jon can decide YES / NO. Pending requests are not execution authorization. Record the exact decision, scope, and decision-source link; never infer approval.

## AQ-001 — Controlled live SerpApi discovery

Status: COMPLETED — the single approved controlled search was consumed and reviewed in Queue #1. No continuing live-provider authorization exists.

Scope completed: one cache-first `search_procurement_intelligence` discovery for the approved rear-wiper query, at most one search, no retries, no destination crawling, no verification, and no compatibility promotion. The result remained DISCOVERED with explicit unknowns.

## AQ-002 — Per-client external-discovery quota protection

Status: COMPLETED — implementation and tests were approved and reviewed. AQ-002 itself did not authorize deployment; deployment occurred only under AQ-003.

The implementation uses exact authenticated client_label + client_fingerprint identity, lifetime configurable caps, durable append-only reservations/settlements in `procurement_usage_events`, conservative unresolved holds, cache-first probes, and measured-attempt accounting.

## AQ-003 — Laptop deployment and durable validation

Status: APPROVED BY JON; EXECUTION COMPLETE; awaiting supervisor review.

Approved scope: deploy AQ-002 protection to the laptop staging runtime with owner=10 and tester-1=5 lifetime caps; preserve hardening; use existing Neon SELECT/INSERT ledger; validate cache/no-provider behavior, missing credentials, client isolation, concurrent enforcement, restart durability, truthful accounting, and ordinary MCP tools; keep SerpApi credentials absent; do not switch production or change schema, dependencies, auth, source policy, public schemas, or registry state.

Result: scope passed. Four tester reservations plus one owner reservation were reconstructed across restart; tester exhaustion and owner isolation passed; exact test reservations were settled at zero; the historical tester hold was preserved; owner HTTP validation passed; actual SerpApi attempts were 0; production identity was unchanged.

Decision source: Jon's explicit AQ-003 approval in the active Codex session on 2026-09-19.

## AQ-004 — Runtime SerpApi activation and new live discovery

Status: NOT REQUESTED / NOT APPROVED.

Do not activate credentials, perform another live search, switch production, publish to the MCP Registry, or migrate to cloud hosting without a new explicit YES / NO decision.

## Request template

- ID and title:
- Status: PENDING
- Concrete requested action:
- Why approval is required:
- Scope and preconditions:
- Risk / quota / cost:
- Alternatives:
- Rollback:
- Jon decision: PENDING
- Decision-source link:


## AQ-006 — Live regression review

Status: PENDING. Local implementation was explicitly approved by Jon and is complete; this is not deployment or live-search authorization. Review docs/aq006-relevance-screening.md and the recorded test results before specifying any temporary deployment and bounded live queries. No real credentials, container actions, or external requests are authorized by this pending entry.

## AQ-007 — Controlled live AQ-006 relevance regression

Status: APPROVED BY JON; BLOCKED at credential prerequisite.

Scope: one owner-authenticated public discovery for `replacement charger` with
caller context MacBook Air / A2681; maximum one external attempt, max_queries=1,
cache-first, no retries, crawling, destination fetches, verification, pagination,
fallback searches, or pooling. Use a separately tagged temporary image/container
from the reviewed AQ-006 patch with existing hardening; keep production and the
original staging runtime unchanged; route ngrok only to temporary staging; clear
credentials and remove only temporary resources; restore production routing; and
publish one sanitized packet only after successful completion.

Preflight found the unchanged owner registry and healthy protected production and
original staging containers, but no secure hidden SerpApi entry was available in
the inherited environment, approved local entries, or matching hidden Keychain
entry. No temporary image/container, provider/account request, ngrok swap, remote
test, quota reservation, or publication occurred. No credential value was printed
or persisted.

Decision source: Jon's explicit AQ-007 approval in the active Codex session.


## AQ-007 — renewed explicit instruction, 2026-09-22

Jon explicitly approved AQ-007 again in the active instruction on 2026-09-22: one controlled live relevance regression using the existing AQ-006 patch including the anchored-prefix correction. This records his decision, not an inferred approval. Latest Issue #1 and remote control files were read; their latest published result is completed AQ-005. The earlier local AQ-007 credential blocker made no live attempt and is superseded for preparation only.

Exact request: query `replacement charger`; device `MacBook Air`; model `A2681`; model_identifier omitted; minimum_evidence `discovered`; refresh_if_missing=true; refresh_if_stale=true. Existing owner identity only, validated by hidden bearer entry before hidden SerpApi entry. One public call, at most one search, max_queries=1, cache-first, no retries/pagination/fallback/destination fetching/crawling/verification; 25-search reserve and fail-closed allowance checks preserved. A hit is zero attempts and is not repeated.

Separately tagged temporary image/container only; preserve production/original staging, hardening, auth, registry and Neon configuration. Disable temporary logging and ngrok inspection; exclusive temporary routing with no pooling, then clear credentials, remove only AQ-007 container, restore localhost:3000 and verify health/routing even on failure. Publish one sanitized AQ-007 packet including blocked outcomes, reconcile control files, then stop APPROVAL_REQUIRED or BLOCKED. This explicit publication instruction supersedes the earlier local “only after successful completion” wording.

state: IN_PROGRESS
task: AQ-007
next_action: Complete prerequisite tests, image equality and hardening checks before live execution.

---



## AQ-007 — explicit approval and completed bounded execution, 2026-09-22

Decision source: Jon's active instruction beginning “Jon explicitly approved AQ-007: one controlled live relevance regression.” No session-message URL is available. Scope: existing AQ-006 patch including anchored-prefix correction; one owner-authenticated public replacement-charger request with MacBook Air/A2681, omitted model identifier, discovered minimum and both refresh flags true; at most one search; cache-first, max_queries=1, no retries or destination fetch/verification; hidden session credentials, temporary hardened image/container and exclusive tunnel, then cleanup and production restore. This records the explicit approval without changing strategic decisions.

The single authorized call completed with one measured search attempt and five unverified leads; owner usage 2 → 3, tester unchanged, reserve preserved, production restored. AQ-007 is execution-complete and APPROVAL_REQUIRED for review. The prior AQ-006 live-review request was authorized only through AQ-007; earlier AQ-007 credential-blocked/preparation status is historical. No ongoing search or production rollout authorization exists. Packet: https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5788153252


## AQ-007 supervisor-reviewed; AQ-008 approved and credential-blocked

Decision source: Jon's active instruction beginning “Jon explicitly approved AQ-008: one outside-agent consumption test,” including “Record AQ-007 as supervisor-reviewed and AQ-008 as approved.” No durable session-message URL is available. AQ-007 is SUPERVISOR-REVIEWED; that review does not verify its leads.

AQ-008 authorizes one existing outside tester-1 agent/client to consume the reviewed AQ-007 image's cache-only response for replacement charger, device MacBook Air, model A2681, omitted model identifier, minimum_evidence discovered, both refresh flags false. Preserve hidden tester credential entry, unchanged registry/database/auth/hardening, browser OFF, SerpApi absent, temporary exclusive routing and cleanup. No owner fallback, provider/destination requests, refresh, additional procurement calls or invented feedback. Publication/reconciliation is authorized; strategy and all remaining gates are unchanged.

Execution stopped because hidden tester-1 entry did not match the unchanged registry. No call, feedback, new usage, temporary runtime, or routing swap occurred; production health and unchanged budgets were verified. Status BLOCKED. Matching existing tester-1 secure entry is the unresolved prerequisite; no rotation or expanded scope is approved. Packet: https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5788351714
