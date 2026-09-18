# Approval Queue

Only Jon can decide YES / NO. Pending requests are not execution authorization.
Record the exact decision, scope, and decision-source link; never infer approval.

## AQ-001 — Activate real SerpApi credential

Status: PENDING

Requested action: securely activate the real SerpApi credential and perform
exactly one controlled live discovery search request after guardrail review.
Use the non-search account quota check, preserve a 25-search reserve, keep
max_queries=1, keep caching enabled, and perform no automatic retries.

Review candidate quality and provenance, conservative compatibility, truthful
search-attempt metering, and remaining free-tier allowance. Discovery permission
does not authorize crawling destinations or treating snippets as product facts.

Why approval is required: this activates a real external credential and may
consume external account allowance.

Preconditions: supervisor / Jon review of the implementation report and known
concurrency limitation; passing required tests; secure credential handling; no
unapproved production or infrastructure changes. Any additional gated runtime
change needs explicit approval within its own stated scope.

Safety: never place the credential or raw private provider payloads in this
public repository or issue. Do not retry a failed controlled search automatically.

Jon decision: PENDING
Decision source: not yet provided.

Do not execute while PENDING.

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
