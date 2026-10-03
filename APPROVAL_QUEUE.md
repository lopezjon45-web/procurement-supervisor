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

### AQ010-CONTROL-INTEGRITY

- **task:** AQ-010 (control plane; not a new task)
- **action:** Documentation-only repair of this repository: current files hold
  current truth only; ROADMAP.md restored as authority; operational details
  removed from current files; START_HERE.md and history/README.md added.
- **status:** CONSUMED
- **exact_scope:** The reviewed diff for README.md, START_HERE.md,
  AI_SUPERVISOR.md, DECISIONS.md, CURRENT_TASK.md, APPROVAL_QUEUE.md,
  CODEX_REPORT.md, ROADMAP.md, AQ-009_CONTROL_SYNC.md, and history/README.md.
- **why_needed:** Current files contradicted each other, the roadmap was
  labelled historical, and operational details were published.
- **risk_cost:** Public documentation only. No runtime, data, or quota effect.
- **evidence_prerequisites:** Remote `main` still at the reviewed baseline.
- **reconciliation:** Jon's direct durable decision approved the reviewed
  scope and status-only reconciliation; both are published as one clean main
  commit with a sanitized message.
- **rollback:** A follow-up commit restoring prior text. No history rewrite.
- **decision:** YES / APPROVED AND CONSUMED
- **durable_decision_source:** https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5974634751

### AQ010-LIVE-MIGRATION-PREFLIGHT

- **action:** Execute the exact read-only migration-history preflight against
  the live database.
- **status:** PENDING (cannot be decided yet)
- **exact_scope:** Read-only catalog / history queries only. No DDL, no DML,
  no temporary objects.
- **why_needed:** Establish the actual migration state before migration 006 is
  designed against it.
- **risk_cost:** Live database access; read-only.
- **evidence_prerequisites:** AQ010-CONTROL-INTEGRITY published and verified;
  the exact query text held in a private reviewed artifact, with a sanitized
  summary and its SHA-256 hash recorded here. The artifact, summary, and hash
  are not yet recorded.
- **rollback:** Not applicable to read-only queries.
- **decision:** PENDING
- **durable_decision_source:** none yet

### AQ010-MIGRATION006-CREATE

- **action:** Create the migration 006 source file.
- **status:** NOT REQUESTED

### AQ010-SLICE1B-ISOLATED-PG-TEST

- **action:** Integration and concurrency validation against an isolated,
  throwaway PostgreSQL database.
- **status:** NOT REQUESTED

### AQ010-SLICE1B-IMPLEMENT

- **action:** Slice 1B product implementation.
- **status:** NOT REQUESTED

### AQ010-PRODUCTION-APPLY

- **action:** Production migration or deployment.
- **status:** NOT REQUESTED

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

AQ-001 through AQ-009 and Slice 1A are CONSUMED or SUPERSEDED. See
[history/README.md](history/README.md).
