# Execution report — Stage 1 (AQ-010)

The filename is legacy; any authorized executor maintains this file. It holds
current Stage 1 evidence and open risks only. Earlier reports are in Git
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
- A successful but empty or all-rejected first discovery does not create an
  accepted head.
- A failed or quarantined refresh cannot replace a same-version admitted head.
  Only same-version, policy-permitted last-known-good is served, explicitly as
  stale with original timestamps.
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

## Slice 1B and Stage 1 completion — 2026-10-04

Statuses are in [CURRENT_TASK.md](CURRENT_TASK.md). Everything below was run by
the executing agent on a development machine. Nothing was deployed, and no
live database was written to. The product workspace is now under local version
control; the accepted state is product commit `b2cc80a`.

### What was built

- **Refresh coordination (Slice 1B).** One claim per request, taken in the
  same transaction as the budget reservation, so concurrent callers for one
  request spend one search. Empty, quarantined, and failed refreshes back the
  request off, doubling on repeats up to 24 hours. Rate-limit, quota, and
  authentication failures cool the provider down for every client. The Python
  bridge refuses to call the provider without a live, unsettled reservation in
  its own database. A result that is stale only because its evidence cannot be
  served no longer triggers a refresh. One new table (migration 006); no
  existing table is altered.
- **One database.** The Node service and the Python bridge now take their
  database from the same setting, so they cannot be configured apart.
- **Readiness.** An authenticated readiness endpoint reports dependency states
  and capabilities. It answers 503 only for PostgreSQL problems; a provider
  outage is reported as degraded. It never calls a provider or writes.
- **Universal search** no longer returns success when no source was asked. Its
  status is success, partial, or unavailable, with reason codes.
- **Relevance screening version 4.** The page's own title or path must name
  the item; discussion sites, forum, question-and-answer, and how-to pages are
  not admitted; a lead naming a different year or model identifier than the
  request is rejected. Request-cache identity carries relevance version 4.

### Tests (passed / failed / skipped)

| Suite | Result | Conditions |
| --- | --- | --- |
| Python, offline | 728 / 0 / 50 | Provider and database doubles. The 50 skips are opt-in PostgreSQL tests. |
| Node, offline | 84 / 0 / 15 | Provider and database doubles. |
| Node, throwaway PostgreSQL | 14 / 0 / 0 | Real local PostgreSQL, databases created and dropped per run, provider stubbed. |
| Python, throwaway PostgreSQL | 14 / 0 / 0 | Same conditions; 10 of these also run offline. |

The throwaway-database runs cover the three conditions the roadmap sets for
Slice 1B: PostgreSQL integration and concurrency (twelve simultaneous callers,
one search), quarantine and refresh backoff, and coordination and fencing
(lease expiry, takeover, and a late finisher that cannot release a claim it no
longer holds). Three of the Node tests run the whole path together: HTTP, the
tool handlers, the budget and claim, the real Python bridge, and cache
storage. Failure-mode tests cover loss of the discovery provider, the
verifier, PostgreSQL, and public ingress.

### Relevance set, real provider

A fixed set of ten queries was run twice through the real service against the
real provider, on a throwaway database: once with screening version 3 and once
with version 4. Each run made ten searches; all twenty were counted, none
unknown. Three queries come from past requests and seven were written by the
executing agent. Links were judged by their addresses only; no page was
opened. Raw results are held privately.

| Query type | Leads, v3 | Leads, v4 | Note |
| --- | --- | --- | --- |
| Vehicle part, with year | 5 | 2 | Forum, question-and-answer, and wrong-year pages dropped. One marketplace listing also dropped as a year conflict; whether it was a good lead is unknown. |
| Laptop charger, with model | 5 | 5 | An editorial page was replaced by a retail category page. |
| Laptop keys, with model | 0 | 4 | The v3 run timed out at the provider (counted, not retried). One v4 lead is for a different product line. |
| Laptop battery, with model | 2 | 0 | Both v3 leads were irrelevant. v4 admits nothing and returns an explicit quarantined error. Unexplained: most provider results did not mention the item. |
| Laptop trackpad, with model | 5 | 3 | Two discussion threads dropped; three retail pages kept. |
| Phone screen | 5 | 5 | A question-and-answer page was replaced by a retail category page. One lead is for a different variant. |
| Vehicle filter, with year | 3 | 3 | Unchanged. |
| Vehicle brake pads, with year | 2 | 2 | Unchanged. |
| Laptop power adapter, with model | 4 | 2 | A search page for a different variant dropped. One marketplace listing also dropped; whether it was a good lead is unknown. |
| Printer ink | 5 | 5 | Unchanged. |

Of the 36 leads admitted under version 3, nine were judged discussion, how-to,
wrong-year, or irrelevant pages. None of the nine is admitted under version 4.

What this does not show: quality beyond these ten queries, any causal claim
about ranking, or whether version 4 loses good leads in general. The provider
appeared to serve its own cached results on the second run, which would make
the comparison like-for-like; that was not confirmed.

## Open limitations

Open risks are listed in [CURRENT_TASK.md](CURRENT_TASK.md). In addition:

- Lexical screening cannot judge model generation, product variant, seller,
  or whether a page is a service rather than a part.
- Numeric-only model numbers are not checked for conflicts.
- Title and snippet rules in version 4 are covered by synthetic fixtures; the
  runs did not retain provider titles or snippets.
- After a crash during a provider call, the same request can be tried again
  once the claim lease expires. The budget slot stays held.
- One non-disclosable record still hides its whole run.
- Capability state is reported by the readiness endpoint only, not inside tool
  responses. That belongs to Stage 2.
