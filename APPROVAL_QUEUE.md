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
