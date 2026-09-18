# Locked Decisions

## Roles

Jon = final YES / NO approval authority.
ChatGPT = strategic supervisor and plan keeper.
Codex = implementation executor.

## Product and operating direction

Build universal procurement intelligence with explicit evidence and unknowns.
Discovery leads are not verified product facts. Compatibility needs evidence.
The laptop-hosted pilot remains the operating direction; cloud migration and
broad publication require approval and demonstrated value.

## Locked sequence

1. SerpApi free-tier quota guardrails.
2. Enable one-search default discovery.
3. Verify real candidate quality.
4. Add per-client discovery quotas.
5. Measure usage and free-tier consumption.
6. Improve only gaps shown by tester evidence.
7. Publish broadly only after value is proven.

Sequence is not execution authorization. Complete review and obtain approvals
before entering a gated step. Do not pursue hypothetical-scale infrastructure.

## Current constraints

- Preserve max_queries=1 in the active intelligence discovery path.
- Preserve no automatic retries.
- Preserve cache-first behavior and provider caching.
- Preserve truthful external_discovery_requests_attempted accounting.
- Retain approximately 25 free-tier searches as a safety reserve; current guard
  uses 25 and must not spend that reserve without explicit approval.
- No real SerpApi credential activation yet.
- No live discovery yet.
- Deeper discovery requires deliberate authorization.

AQ-001 remains PENDING. No decision in this document approves it.

## Work-cycle outcome

Each cycle must end in exactly one of CONTINUE, APPROVAL_REQUIRED, or BLOCKED,
with the meaning defined in AI_SUPERVISOR.md.
