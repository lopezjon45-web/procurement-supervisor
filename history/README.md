# History index

**Not authority.** This index summarizes past milestones so readers can find
the full record. Nothing here authorizes current work; current state is in the
control files listed in [START_HERE.md](../START_HERE.md).

Full records are in Git history (commits below) and in
[Supervisor Issue #1](https://github.com/lopezjon45-web/procurement-supervisor/issues/1).
Some older records contain operational details that current files deliberately
omit. Do not copy them forward. Approvals below were recorded from agent
sessions; most have no direct durable Jon source.

| Milestone | Outcome | Commits |
| --- | --- | --- |
| Setup | Six control files and permanent Issue #1 created. | `2c1a283` |
| SERPAPI-FREE-TIER-GUARDRAIL-001 | Provider free-tier guardrail implemented and reviewed. | `48a9544` |
| AQ-001 | One controlled live discovery; result DISCOVERED with explicit unknowns. Consumed. | `f5728e4` |
| AQ-002 | Per-client discovery quotas with durable reservations and settlements. Implemented and reviewed. | `0e9e0aa` |
| AQ-003 | Hardened staging deployment; provider-free validation of durable quotas. | `2713e5d`, `87e5a2e`, `8d42f74`, `2b04377` |
| AQ-004 | One controlled public staging discovery; five unverified leads. Reviewed. | `7b15cca` |
| AQ-005 | Bounded candidate-quality measurement: one eligible query; leads were off-topic or indeterminate. | `877ba17`, `f30821c` |
| AQ-006 | Local deterministic relevance screening and request-cache version 2. | recorded in `2eaa19b` |
| AQ-007 | One controlled live relevance regression; better visible topical mix, not causally attributed. Reviewed. | `2eaa19b`, `0e933fc` |
| AQ-008 | Outside-agent consumption test. First attempt blocked on a credential mismatch; later completed after a reported tester credential rotation. Stale, non-actionable leads exposed the relevance gap. Rotation provenance incomplete. | `0e933fc`, `df64791` |
| AQ-009 | Stage 0 architecture resilience baseline (ROADMAP.md, ARCHITECTURE_RESILIENCE.md). Accepted and closed. | `df64791` |
| AQ-010 Slice 1A | Stage 1 cache/relevance integrity; completed and supervisor-reviewed. | `7d31589`, `4d6104a`, `9127235`, `0591180` |
| Cross-cutting gates | Universal Agent Governance Harness and Secure Agent Handshake recorded as approved direction. | `34130a5` |
| Control-plane repair | AQ010-CONTROL-INTEGRITY approved and published; history removed from current files and indexed here. | `228daac` |
| Repository cleanup | Duplicate and stale text removed; AQ-009_CONTROL_SYNC.md retired (in Git history at `228daac`). | pending |
