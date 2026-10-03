# Execution report — AQ-010

The filename is legacy; any authorized executor maintains this file. It holds
current AQ-010 evidence and open risks only. Earlier reports are in Git
history and Issue #1; see [history/README.md](history/README.md).

## Slice 1A — COMPLETED / SUPERVISOR-REVIEWED

Accepted behavior (local product implementation):

- One deterministic lead screen is shared by the provider adapter and the
  request-cache admission gate, and runs before head promotion. Recognized
  retail search routes may use named search terms. Synthetic AQ-005 / AQ-007
  URL-shape regressions reject known off-topic and video/discussion shapes and
  leave opaque or informational shapes indeterminate. Screening selects leads
  only; it verifies no product, seller, price, stock, or compatibility fact.
- Request-cache identity is version 3, with explicit planner and relevance
  versions. Older runs and heads stay stored but cannot serve as version-3
  last-known-good.
- `content_state` values: `miss`, `fresh`, `stale_servable`, `hard_stale`,
  `quarantined`. Fresh lasts 24 hours, stale_servable at most 24 more, then
  hard_stale. Stricter stored or current SourcePolicy limits win.
- A failed or quarantined refresh cannot replace a same-version admitted head.
  Policy-permitted last-known-good is served explicitly as stale, with
  original timestamps unchanged.
- Empty-success correction: a successful but empty or all-rejected first
  discovery does not create an accepted request-cache head.
- Rejected candidates do not enter current intelligence records. Only typed
  aggregate counts and safe reason codes persist.
- Additive response fields: `content_state`, `content_reason_code`,
  `screening_summary`, `provider_screening_summary`, `refresh_outcome`,
  `served_last_known_good`. Tool names, public inputs, and legacy status /
  cache-status values are unchanged.
- Bounds unchanged: one query, 20 rows inspected, five leads, no automatic
  retry.

Contract document: `docs/aq010-slice1a.md` in the product workspace. On
2026-10-03 it was confirmed present and consistent with the states, version-3
identity, and 24 h + 24 h windows above.

## Validation and provenance

| Run | Python | Node (safe MCP/HTTP) | Source |
| --- | --- | --- | --- |
| Pre-change baseline | 666 / 0 / 46 | 54 / 0 / 0 | [5882441121](https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5882441121) |
| Initial implementation | 675 / 0 / 46 | 57 / 0 / 0 | [5882441121](https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5882441121) |
| After state-label correction | 677 / 0 / 46 | 57 / 0 / 0 | [5882580787](https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5882580787) |
| **Accepted**, after empty-success correction | **682 / 0 / 46** | **57 / 0 / 0** | [5893841375](https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5893841375) |

Counts are passed / failed / skipped from separate runs; they are not
additive. The 46 skips are opt-in PostgreSQL tests. The opt-in PostgreSQL
fixture creates and drops a database, so it was not run.

The 675 and 677 runs denied all networking for Python and allowed loopback
only for Node, with provider and database doubles. The accepted 682 record
does not state the command, the network and database conditions, or the files
changed by the empty-success correction. The product workspace is not under
version control, so the accepted source state is not pinned to a commit.

## Open limitations

- Real PostgreSQL integration and concurrency are unvalidated.
- Lexical screening can miss useful opaque or informational leads and can
  admit keyword-stuffed ones.
- Repeated refresh after quarantine can still occur, and spend quota, until
  Slice 1B coordination and backoff exist.
- Live relevance evidence is one repeated query. It must not be presented as
  proof of broad quality.

## Slice 1B — current state

- Design and supervisor review only. Implementation, migration 006 creation,
  and migration 006 application are not approved.
- A corrected V2 design was reported as prepared, with two changes:
  `pre_dispatch_zero` removed and provider-global cooldown ordering corrected.
  No durable record of the design exists yet; these are reported, not
  evidenced.
- An exact read-only migration-history preflight was reported as prepared. It
  has NOT been executed, its text is not published, and it is not approved.

## Current cycle — control-plane integrity repair

Documentation-only repair reviewed against remote `main`
`34130a559784c5b8e0f1e5e62db57278997141e8`. Jon directly approved
AQ010-CONTROL-INTEGRITY at
https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5974634751.
The reviewed repair and status reconciliation were published as one clean
main commit. No product, runtime, database, provider, credential, auth,
dependency, container, or routing action occurred. No SQL was executed.

```text
state: APPROVAL_REQUIRED
task: AQ-010
next_action: Return to Slice 1B V2 design and supervisor review; record the design and exact preflight text as a private reviewed artifact with a public summary and hash.
```
