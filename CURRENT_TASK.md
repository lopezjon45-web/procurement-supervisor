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
| Live read-only migration-history preflight | REVISION REQUIRED / NOT EXECUTED / NOT APPROVED |

## Review artifacts

The Slice 1B V2 design packet and the read-only migration-history preflight
exist as private artifacts. Review on 2026-10-04 found the preflight needs
revision before it can be approved (explicit role checks, hard stop
conditions, lock and idle timeouts, connection path). Revised artifacts, their
SHA-256 hashes, and a sanitized summary will be recorded here.

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

1. Record the revised design and preflight hashes and a sanitized summary here
   for supervisor review.
2. Jon decides YES / NO on AQ010-LIVE-MIGRATION-PREFLIGHT for that exact hash.
