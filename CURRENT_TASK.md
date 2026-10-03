# Current task

```text
task: AQ-010 — Cache/Relevance Integrity
roadmap_stage: 1
state: APPROVAL_REQUIRED
```

AQ-010 is the sole active task. Jon remains the final YES / NO authority.

| Item | Status |
| --- | --- |
| Slice 1A | COMPLETED / SUPERVISOR-REVIEWED |
| Slice 1B | DESIGN / SUPERVISOR REVIEW ONLY (non-gated review activity) |
| Slice 1B implementation | NOT APPROVED |
| Migration 006 creation | NOT APPROVED |
| Migration 006 application | NOT APPROVED |
| Live read-only migration-history preflight | PREPARED (reported) / NOT EXECUTED / APPROVAL REQUIRED |
| Control-plane integrity repair | COMPLETED / APPROVED / PUBLISHED (AQ010-CONTROL-INTEGRITY) |

## Evidence gap

A corrected Slice 1B "V2" design and a read-only migration-history preflight
were reported as prepared in the supervisor workstream. On 2026-10-03, neither
had a durable record in this repository, in Supervisor Issue #1, or in the
local product workspace. Until they are published for review, they are
reported work, not current evidence, and no decision can rest on them.

## Current prerequisite

Record the corrected Slice 1B V2 design and exact preflight query text in a
private reviewed artifact, with a public sanitized summary and SHA-256 hash,
before the live read-only database preflight is considered for approval.

## Open risks

- Real PostgreSQL integration and concurrency are unvalidated.
- Repeated refresh after quarantine may spend quota until Slice 1B
  coordination/backoff is implemented and validated.
- Live relevance evidence is narrow and is not proof of broad quality.

## Stop boundary

This state authorizes no product or runtime code change, SQL against any live
database (read-only included), migration creation or application, provider
call, container or routing change, credential or auth change, dependency,
SourcePolicy change, harness installation, or handshake implementation.

## Next action

1. Put the corrected Slice 1B V2 design and the exact preflight query text in
   a private reviewed artifact; record a sanitized summary and SHA-256 hash
   here for supervisor review.
2. Jon decides YES / NO on AQ010-LIVE-MIGRATION-PREFLIGHT for that hash.
