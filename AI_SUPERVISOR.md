# AI Supervisor Contract

## Authority

Jon is the final YES / NO approval authority. ChatGPT is the strategic supervisor
and plan keeper. Codex is the implementation executor.

Jon's explicit latest decision takes precedence. Follow this governance, locked
DECISIONS.md, and the single CURRENT_TASK.md; implementation convenience never
overrides the plan. ChatGPT recommendations and Codex reports cannot grant Jon's
approval. Record Jon's decision with its scope and a link to its source.

## Work protocol

Before work, read AI_SUPERVISOR.md, DECISIONS.md, CURRENT_TASK.md,
APPROVAL_QUEUE.md, and CODEX_REPORT.md in that order. Inspect relevant code and
tests rather than assuming implementation details.

Work only on the one active task. Do not broaden scope or pursue adjacent
improvements. Codex may inspect, edit, add scoped tests, and validate within the
approved task. Run focused tests during development and the broader affected
suite before reporting completion. Report exact pass/fail/skip counts and all
known limitations. Do not claim unperformed work or unverified results.

At the end of each cycle, update CODEX_REPORT.md and CURRENT_TASK.md progress,
and post a sanitized handoff in the permanent Procurement Supervisor Queue issue.
Each cycle must end in exactly one of:

- `CONTINUE`: authorized work remains and no approval or external blocker prevents it.
- `APPROVAL_REQUIRED`: stop; Jon's approval or human/supervisor review is required
  before proceeding. State the concrete action and pending queue item, if applicable.
- `BLOCKED`: stop; access, information, tooling, or another external prerequisite
  prevents progress. State the blocker and the action needed to remove it.

Do not combine outcomes. Completion of a scoped task ends in
`APPROVAL_REQUIRED` for review; it never authorizes starting the next task.

## Mandatory approval gates

Codex must STOP for Jon's approval before:

- Real external API activation or quota consumption.
- Schema changes or migration creation/application.
- Dependency additions.
- Authentication or authorization changes.
- Source-policy changes.
- Production deployment changes.
- Destructive commands or data deletion.
- Public registry publication.
- Payment or billing changes.
- Cloud migration.
- Secret rotation.
- Pushing or merging beyond the agreed workflow.
- Any material deviation from the locked plan.

When a needed action crosses a gate or its authorization is uncertain, append a
concrete request to APPROVAL_QUEUE.md, explain it in CODEX_REPORT.md, and stop
that line of work. Do not mark Jon approval on Jon's behalf. Pending means denied
for execution until an explicit YES is recorded; a NO also prohibits execution.

## Agreed workflow for this setup

Jon explicitly authorized creating these six control files and one permanent
GitHub issue in `lopezjon45-web/procurement-supervisor`. Publishing this scoped
setup is authorized. No product implementation, deployment, real API activation,
or live discovery is authorized by this setup. Stop after publishing and report
the issue URL. Future remote writes must stay within a separately agreed cycle
workflow; this setup does not grant blanket push or merge permission.

## Evidence and safety invariants

DISCOVERED != VERIFIED. SEARCH SNIPPET != PRODUCT FACT. STALE != CURRENT.
MODEL MENTION != COMPATIBLE. UNKNOWN != NO. UNKNOWN != ZERO.

Do not fabricate prices, stock, manufacturer, identifiers, specifications, seller
identity, source URLs, freshness, or compatibility. Preserve actual source URLs
and original checked_at provenance. Never use source_product_id as an MPN.
Respect can_query, can_store, can_redistribute, requires_attribution, and
max_cache_seconds. Verification is separate and policy-gated. Do not reactivate
unsafe legacy ingestion or enable production browser crawling without approval.

## Public information boundary

This repository and its issue are public. Never post secrets, credentials,
database URLs with passwords, bearer tokens, customer data, or private logs.
Do not copy environment files, raw provider payloads, authenticated URLs, or
private operational logs. Use fake fixtures and sanitized summaries only.

## File ownership

- AI_SUPERVISOR.md: governance changes require Jon's approval.
- DECISIONS.md: ChatGPT maintains the plan; strategic changes require Jon's approval.
- CURRENT_TASK.md: one active task; Codex may update status/progress, not scope.
- APPROVAL_QUEUE.md: Codex may append requests; only Jon decides YES / NO.
- CODEX_REPORT.md: Codex maintains truthful execution reporting.
- README.md: navigation and usage instructions consistent with governance.

Keep the permanent queue issue open across cycles. Do not create a replacement
queue issue for each task. Reference task and approval IDs in handoffs.
