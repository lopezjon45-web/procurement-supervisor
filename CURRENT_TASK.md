# Current Task

## AQ-005 — Bounded candidate-quality measurement

Status: APPROVED; documentation sync complete; evidence selection and execution pending.

AQ-005 is EXPLICITLY APPROVED BY JON ON 2026-09-21. Decision source: Jon's instruction beginning “AQ-005 is explicitly approved by Jon on 2026-09-21” in the active Codex session. This records Jon's decision, not an approval inferred by Codex. This documentation-only sync precedes AQ-005 execution.

## Previous milestone

AQ-004 is COMPLETED AND REVIEWED, as explicitly directed by Jon on 2026-09-21 in the active Codex session. Its single public test recorded one external search attempt and five discovered/unverified leads, all compatibility unknown. Account readings were 244 before and after; observed delta zero is not a billing/cache determination. Owner durable usage became 1/10; tester history was unchanged. Credentials were cleared, the temporary container removed, and production tunnel/health restored without changing the production container/image. Result: https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5753722005 . This reviewed status does not establish candidate compatibility or broad procurement usefulness.

## Approved scope and stop boundary

Owner client only; baseline usage 1/10. Tester-1 must remain untouched. Select up to three distinct real procurement queries from existing tester-demand evidence, excluding AQ-004's rear-wiper query. Do not invent demand or pad the sample: use fewer when fewer suitable uncached queries exist. Each selected query gets at most one public MCP discovery call with refresh_if_missing=true, refresh_if_stale=true, minimum_evidence=discovered, and max_queries=1 per provider request. Cache hits consume zero and must be reported without repeating the query. No retries, second search per query, crawling, destination fetches, verification, or compatibility promotion.

Use a temporary staging-only container from the existing pinned hardened staging image. Preserve UID 10001, read-only filesystem, dropped capabilities, no-new-privileges, tmpfs restrictions, memory/CPU/PID limits, loopback binding, unchanged Neon configuration and client registry, and browser crawling OFF. Production container/image remain unchanged. Hidden local entry and inherited runtime environment only for SERPAPI_API_KEY; never print or put the value in chat, arguments, files, images, or logs. Temporarily expose only staging through ngrok, without pooling or host-header override. Clear the key, remove only the temporary AQ-005 container, restore ngrok to localhost:3000, and verify production health and endpoint identity.

Report each query's cache state, actual external attempts, lead count, source-type/relevance observations, and explicit unknowns without compatibility claims. Keep provider account readings separate from measured attempts; preserve the 25-search reserve as far as actual attempts allow. Verify no usage double-counting. Publish one sanitized AQ-005 packet to Supervisor Issue #1, then stop for review.

## Truth rules and limitations

DISCOVERED != VERIFIED; SEARCH SNIPPET != PRODUCT FACT; STALE != CURRENT; MODEL MENTION != COMPATIBLE; UNKNOWN != NO. Unknown facts remain null/unknown. Preserve exact source URLs, discovery versus checked timestamps, and all SourcePolicy permissions. Never use source_product_id as an MPN. No product/schema/dependency/auth/source-policy/public-schema/cloud/registry changes are authorized. Account checks are non-atomic against other consumers and may lag. Lifetime caps and conservative unresolved holds remain unchanged.

## Historical AQ-003 task record (superseded status only)

# Current Task

## ID

AQ-003 — Laptop deployment and durable per-client discovery validation

## Status

Jon-approved AQ-003 scope is complete and awaiting supervisor review. Production was not switched. No SerpApi credential is present in the runtime, and no AQ-004 work started.

## Objective

Deploy the AQ-002 per-client external-discovery protection to the laptop MCP staging runtime, preserve hardening, and validate durable quota behavior without provider activity.

## Approved scope

- Lifetime pilot caps: owner=10 searches; tester-1=5 searches.
- Rebuild/deploy staging while preserving the existing hardened container.
- Use the existing Neon `procurement_usage_events` table with SELECT/INSERT only.
- Validate cache/no-provider behavior, missing credentials, client isolation, concurrent enforcement, restart durability, truthful accounting, and ordinary MCP tools.
- Keep browser crawling OFF and SerpApi credentials absent.
- Do not change schema, dependencies, auth, source policy, public tool schemas, production, or public registry state.

## Evidence completed

- Preflight confirmed Neon connectivity and ledger read/append permissions.
- Registry identities and caps were present: owner=10, tester-1=5.
- Container hardening remained present: UID 10001, read-only filesystem, dropped capabilities, no-new-privileges, resource limits, loopback-only binding, and production browser crawling OFF.
- Cache-only calls returned zero external attempts. Ordinary MCP tools remained functional.
- Six refresh attempts (four tester-1, two owner) returned `missing_credentials` with zero actual SerpApi search attempts. No provider credential was present.
- Four tester-1 reservations and one owner reservation were committed before any provider-capable subprocess. A fifth tester-1 admission was denied; owner remained isolated.
- After staging restart, Neon reconstruction reported tester-1 held=5 (four AQ-003 holds plus one historical hold), owner held=1, tester exhaustion, owner remaining=9, and zero actual searches.
- Recovery appended exactly five zero-attempt settlements. The historical tester-1 hold was preserved. Post-recovery totals returned to owner consumed=0/held=0 and tester-1 consumed=0/held=1.
- Owner-authenticated loopback HTTP validation succeeded: initialize, all four tools, cache-only search with zero external attempts, and ordinary inventory access.

## Deployment status

The staging/validation runtime was restarted and healthy. Production remained on its original runtime/image; production identity was unchanged. No public MCP switch or ngrok publication was performed.

## Limitations

This was a provider-free pilot validation. No new SerpApi search was authorized or attempted in AQ-003. The durable concurrency/isolation exercise used the real Neon ledger through the quota module; the hold/restart harness was not a broad public-HTTP load test. Unresolved holds intentionally do not expire automatically. The caps are lifetime pilot caps, not periodic resets. Older workers or direct non-remote paths remain outside this boundary.

## Next action

Supervisor review of this completed AQ-003 packet only. Do not start AQ-004, activate SerpApi, switch production, publish to the MCP Registry, or migrate to cloud hosting without a new explicit approval.

## Cycle outcome

APPROVAL_REQUIRED
