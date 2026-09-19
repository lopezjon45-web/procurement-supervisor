# Codex Report

## Cycle

AQ-003 — laptop deployment and durable per-client discovery validation.

## Scope and changes

The Jon-approved AQ-003 deployment was completed on the staging/validation runtime only. The AQ-002 quota implementation was packaged into the hardened image with its required runtime modules. The production container was not switched or restarted. No product source, schema, dependency, authentication, source policy, public tool schema, or browser-crawling policy was changed during validation.

Configured lifetime pilot caps were owner=10 and tester-1=5. The existing Neon `procurement_usage_events` table was used with the application role's existing SELECT/INSERT permissions; no migration or destructive data operation occurred.

## Validation results

- Neon host and ledger permissions: passed; readable and appendable.
- SerpApi credential present in runtime: false.
- Container hardening: preserved (UID 10001, read-only filesystem, all capabilities dropped, no-new-privileges, resource limits, loopback-only binding, browser crawling OFF in production).
- Cache/no-provider calls: passed for both identities; zero external search attempts.
- Ordinary MCP tools: passed; all four tools were listed and inventory access succeeded.
- Missing-credentials checks: six refresh attempts (four tester-1 and two owner) returned `missing_credentials`; actual SerpApi attempts remained 0.
- Durable concurrent admission: four tester-1 reservations admitted, the fifth denied at the cap boundary; one owner reservation admitted independently.
- Restart durability: staging restarted healthy; Neon reconstruction showed tester-1 held=5 (one historical hold plus four AQ-003 holds), owner held=1, tester exhausted, owner remaining=9, and 0 actual searches.
- Recovery: exactly five tagged AQ-003 reservations were settled with measured attempts=0. The historical tester-1 hold was not touched. Final totals were owner consumed=0/held=0 and tester-1 consumed=0/held=1.
- Owner-authenticated HTTP: initialize succeeded; the four frozen tools were returned; cache-only `search_procurement_intelligence` returned miss/not_invoked/0 attempts; `get_market_procurement_intelligence` returned success.

## Deployment status

Staging is healthy and validated. Production identity remained unchanged and was not switched. No public MCP/ngrok publication was performed. No SerpApi key was activated or persisted.

## Accounting and safety

Reservations and settlements remain distinct append-only ledger events. Zero-attempt provider-free outcomes did not consume quota, and no usage double-counting was observed. Unknown historical outcomes remain conservative holds. No deletes, updates, blanket cleanup, schema changes, or retries were used.

## Limitations

AQ-003 intentionally performed no new provider search, so it does not measure candidate quality. The controlled concurrency/isolation exercise used the real Neon ledger through the quota module; it was not a broad public-HTTP load test. Holds do not expire automatically. Caps are lifetime pilot caps, not periodic resets. Old workers or direct Python/stdio paths outside the remote HTTP boundary are not protected by this deployment.

## Stop state

AQ-003 is complete within the approved scope and awaits supervisor review. AQ-004 (runtime SerpApi activation and a new live discovery) is not approved.

state: APPROVAL_REQUIRED
task: AQ-003
summary: Hardened staging deployment and provider-free Neon-backed quota validation passed; production unchanged.
next_action: Supervisor review only.
