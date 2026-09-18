# Approval Queue

Only Jon can decide YES / NO. Pending requests are not execution authorization.
Record the exact decision, scope, and decision-source link; never infer approval.

## AQ-001 — Activate real SerpApi credential

Status: APPROVED

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

Jon decision: APPROVED for the narrow scope below.
Decision source: Jon's explicit “AQ-001 APPROVED BY JON” instruction in the active Codex session on 2026-09-18. The approval is also recorded in Procurement Supervisor Queue #1.

### Approved execution scope — 2026-09-18

- Exactly one controlled live SerpApi search through the existing procurement intelligence path.
- Query: "I need a rear wiper arm for a 2015 Ford Edge".
- `refresh_if_missing=true`, `minimum_evidence=discovered`, `max_queries=1`; cache-first behavior remains in force.
- Account/quota API checks are allowed and do not count as search requests.
- Preserve the 25-search reserve. Stop if allowance is at or below 25, quota check fails, credential/authentication fails, or the search errors.
- No retries and no second search. No destination-page crawling or product verification; candidates remain DISCOVERED and compatibility must not be inferred.
- Session-only secret entry if needed; do not persist or expose the credential.
- No deployment/runtime restart, schema, authentication, source-policy, or dependency changes; no product-code changes or next roadmap step.
- Post one sanitized controlled-attempt result to Queue #1, then stop for supervisor review.

This approval authorizes only this controlled attempt; it is not continuing live-provider authorization.

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
