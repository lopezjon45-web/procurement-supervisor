# Execution report — AQ-010

The filename is legacy; any authorized executor maintains this file. It holds
current AQ-010 evidence and open risks only. Earlier reports are in Git
history and Issue #1; see [history/README.md](history/README.md).

## Slice 1A — COMPLETED / SUPERVISOR-REVIEWED

Accepted behavior, in brief (full contract: `docs/aq010-slice1a.md` in the
product workspace):

- Deterministic lead screening runs before request-cache head promotion. It
  selects leads only and verifies no product, seller, price, stock, or
  compatibility fact.
- Request-cache identity is version 3. `content_state` is `miss`, `fresh`
  (24 h), `stale_servable` (at most 24 h more), `hard_stale`, or `quarantined`;
  stricter SourcePolicy limits win.
- A failed, quarantined, or empty refresh never replaces an admitted head.
  Last-known-good is served explicitly as stale with original timestamps.
- Tool names, public inputs, and bounds (one query, 20 rows, five leads, no
  automatic retry) are unchanged.

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

Open risks are listed in [CURRENT_TASK.md](CURRENT_TASK.md). In addition,
lexical screening can miss useful opaque or informational leads and can admit
keyword-stuffed ones.

## Slice 1B — current state

Design and supervisor review only; see [CURRENT_TASK.md](CURRENT_TASK.md).
Implementation and migration 006 are not approved. The preflight has not been
executed.
