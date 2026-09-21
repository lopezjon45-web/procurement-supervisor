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
