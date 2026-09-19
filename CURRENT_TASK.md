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
