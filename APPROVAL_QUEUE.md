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
