# Approval queue

Only Jon decides. A request may be executed only while its status is APPROVED,
only within its exact scope, and only with a durable decision source as
defined in [AI_SUPERVISOR.md](AI_SUPERVISOR.md). Approval of one request never
transfers to another.

## Status values

| Status | Meaning |
| --- | --- |
| NOT REQUESTED | Known future gate; no request made; execution prohibited |
| PENDING | Requested; awaiting Jon; execution prohibited |
| APPROVED | Jon said YES to the exact scope; executable within it |
| DENIED | Jon said NO; execution prohibited |
| CONSUMED | Approved scope fully used; no further authority |
| SUPERSEDED | Replaced by a later request or decision |

## Request template

```text
request_id:
task:
action:
status:
exact_scope:
why_needed:
risk_cost:
evidence_prerequisites:
rollback:
decision:
durable_decision_source:
```

## Non-gated activity

- **Slice 1B V2 design and supervisor review.** Review work only, with no
  runtime, database, or implementation effect, so it needs no gate. It cannot
  conclude until the design is in a durable reviewed record (a private
  artifact plus a public sanitized summary and content hash is acceptable).
  Implementation and migration work remain gated below.

## AQ-010 requests

### AQ010-LIVE-MIGRATION-PREFLIGHT

- **action:** Execute the exact read-only migration-history preflight against
  the live database.
- **status:** PENDING (cannot be decided yet)
- **exact_scope:** Read-only catalog / history queries only. No DDL, no DML,
  no temporary objects.
- **why_needed:** Establish the actual migration state before migration 006 is
  designed against it.
- **risk_cost:** Live database access; read-only.
- **evidence_prerequisites:** The revised query text in a private reviewed
  artifact, with a sanitized summary and its SHA-256 hash recorded here. Not
  yet recorded; the first version was found to need revision.
- **rollback:** Not applicable to read-only queries.
- **decision:** PENDING
- **durable_decision_source:** none yet

### Future AQ-010 gates (NOT REQUESTED)

- **AQ010-MIGRATION006-CREATE:** create the migration 006 source file.
- **AQ010-SLICE1B-ISOLATED-PG-TEST:** integration and concurrency validation
  against an isolated, throwaway PostgreSQL database.
- **AQ010-SLICE1B-IMPLEMENT:** Slice 1B product implementation.
- **AQ010-PRODUCTION-APPLY:** production migration or deployment.

## Housekeeping requests (not tasks)

### PUBLIC-ENDPOINT-EXPOSURE

- **action:** Review whether the previously published pilot endpoint should be
  retired or rotated before the next public authenticated test, and if so
  prepare a separately scoped runtime-change approval request.
- **status:** PENDING
- **why_needed:** Earlier control files and Issue #1 packets published the
  pilot tunnel locator and runtime metadata. Removing them from current files
  does not remove them from Git history or Issue #1; treat them as exposed.
- **exact_scope:** Decision/review only. No runtime, tunnel, DNS, routing,
  credential, or deployment change is authorized by this request.

### AQ008-ROTATION-PROVENANCE

- **action:** Jon ratifies, or declines to ratify, the reported AQ-008 tester
  credential rotation.
- **status:** PENDING
- **why_needed:** The rotation is recorded only from a supplied handoff, with no
  direct durable source. The tester identity's current label and cap are not
  independently confirmed.
- **durable_decision_source:** historical approval reported; direct durable
  source unavailable. Absence of ratification does not establish that the
  rotation was unauthorized.

## Future gates (approved direction only)

- **HARNESS-INSTALL:** NOT REQUESTED. Needs a reviewed merge/collision plan.
- **SECURE-HANDSHAKE-DESIGN** and **SECURE-HANDSHAKE-IMPLEMENT:** NOT REQUESTED.

## Closed requests

AQ-001 through AQ-009, Slice 1A, and AQ010-CONTROL-INTEGRITY
([decision](https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5974634751))
are CONSUMED or SUPERSEDED. See [history/README.md](history/README.md).
