# AI Supervisor Contract

Binding governance for every person and agent working in this repository.
Begin from [START_HERE.md](START_HERE.md).

## Authority and roles

- **Final authority: Jon.** Only Jon decides YES / NO on an approval gate. His
  latest direct durable decision is the highest authority. When the control
  files have not yet been reconciled to that decision, execution stops
  (`BLOCKED`) until they are. Decisions reported without a direct durable
  source do not outrank the control files.
- **Strategic supervisor / reviewer:** the person or agent Jon designates for
  the current cycle. The supervisor keeps the plan, reviews work, and
  recommends. A recommendation is never approval.
- **Executor:** any agent Jon has explicitly authorized for the current task.
  The executor works only within the active approved scope.

ChatGPT, Codex, and Claude are examples of agents that have filled these
roles; no role belongs to a vendor. No agent may infer, manufacture, backdate,
or expand Jon's approval, and no agent may approve its own work.

## Decision sources

Record every Jon decision with its exact scope and a link to its source.

**New gated actions.** Link a direct durable source before execution. The
preferred source is Jon's own YES / NO comment on
[Supervisor Issue #1](https://github.com/lopezjon45-web/procurement-supervisor/issues/1)
or another durable record Jon controls. An executor's statement that Jon
approved something in another session is not, by itself, a direct source.

**Identity caveat.** Agent handoffs are currently posted from the same GitHub
account Jon uses. A comment from that account therefore shows only that Jon's
credentials were used, not that Jon wrote it. Until agents post from a separate
identity:

- Jon's decisions begin with the exact line `JON DECISION:`.
- Agents never post or edit a comment beginning with that line.
- Agent comments begin with `Agent handoff —` and name the task and role.

This convention is not proof of authorship. A separate agent identity would
be the stronger fix; it has not been requested.

**Post-decision reconciliation.** A reviewed change records its own decision
as PENDING. After Jon's direct durable decision names the exact reviewed
commit, one reconciliation commit updates only the status lines and decision
links to match that decision. The reconciled tree is what gets merged. Merge
with a squash or clean commit and a sanitized message, so proposal-branch
commits and their metadata do not enter `main`'s ancestry.

**Private review artifacts.** Exact material that should not be public (for
example database queries or internal schema detail) may stay in a private
reviewed artifact. The public record then carries a sanitized summary and the
artifact's SHA-256 content hash, and the decision names that hash.

**Historical actions.** Where no direct durable Jon source exists, label the
provenance "historical approval reported; direct durable source unavailable".
Never fabricate or backdate a source.

## Work protocol

1. Resolve current remote state: fetch and record the remote `main` SHA.
2. Verify the single active task in CURRENT_TASK.md and the exact approval in
   APPROVAL_QUEUE.md. Missing or inconsistent authority: stop `BLOCKED`.
3. Do only the bounded, approved work. Inspect real code and tests rather than
   assuming. Do not broaden scope or pursue adjacent improvements.
4. Validate: focused tests during development, the broader affected suite
   before reporting. Report exact pass / fail / skip counts, the command, and
   the conditions (network access, database opt-ins).
5. Prepare a sanitized reconciliation of the control files.
6. Review the change against the approved scope and the public information
   boundary.
7. Obtain any required commit / push approval.
8. Publish without rewriting history: no force-push, no amending published
   commits, no deleting records.
9. Reconcile status lines to the decision, then verify the remote SHA, the
   exact changed files, and the remote file contents.
10. Only then advance, and post one sanitized handoff to Issue #1.

Report truthfully. Never claim unperformed work or unverified results. Keep
measured, reported, and unknown values distinct.

## Cycle outcomes

Each cycle ends in exactly one of:

- `CONTINUE`: authorized work remains and nothing blocks it.
- `APPROVAL_REQUIRED`: stop; Jon's decision or supervisor review is needed.
  Name the action and the queue item.
- `BLOCKED`: stop; access, information, tooling, or authority is missing.
  Name the blocker and what would remove it.

Do not combine outcomes. Completing a task ends in `APPROVAL_REQUIRED`; it
never authorizes the next task.

## Mandatory approval gates

Stop for Jon's explicit, recorded YES before:

- real external API activation or quota consumption;
- executing SQL against any live or shared database, including read-only queries;
- schema changes or migration creation / application;
- dependency additions;
- authentication or authorization changes;
- provider credential entry, credential rotation, or secret rotation;
- source-policy changes;
- production deployment, container, or public-routing changes;
- destructive commands or data deletion;
- public registry publication;
- payment or billing changes;
- cloud migration;
- installing the Universal Agent Governance Harness or implementing the Secure
  Agent Handshake;
- committing, pushing, or merging to this repository outside an approved cycle;
- any material deviation from DECISIONS.md or ROADMAP.md.

When an action crosses a gate, or its authorization is uncertain, add a request
to APPROVAL_QUEUE.md, explain it in CODEX_REPORT.md, and stop that line of
work. PENDING means no execution; DENIED prohibits execution. Approval of one
gate never transfers to another.

## Evidence invariants

DISCOVERED != VERIFIED. SEARCH SNIPPET != PRODUCT FACT. STALE != CURRENT.
MODEL MENTION != COMPATIBLE. UNKNOWN != NO. UNKNOWN != ZERO.
AUTHENTICATED != AUTHORIZED.

Do not fabricate prices, stock, manufacturer, identifiers, specifications,
seller identity, source URLs, freshness, or compatibility. Preserve actual
source URLs and original checked_at provenance. Never use source_product_id as
an MPN. Respect can_query, can_store, can_redistribute, requires_attribution,
and max_cache_seconds. Verification is separate and policy-gated. Do not
reactivate unsafe legacy ingestion or enable production browser crawling
without approval.

## Public information boundary

This repository and Issue #1 are public, and their Git and edit histories are
permanent. Never publish secrets, credentials, database URLs, bearer tokens,
customer data, raw provider payloads, environment files, or private logs.

Do not publish operational targeting material either, even when it is not
technically a secret:

- public tunnel or endpoint hostnames, and other service locators;
- local upstream addresses and ports;
- process IDs, container IDs, and image digests or tags tied to live runtimes;
- client or token fingerprints and token hashes;
- credential storage or entry mechanics (keychain, service, or account names);
- local usernames, machine names, and filesystem paths;
- per-identity ledger balances or history, unless essential to a current
  public policy decision;
- private runtime topology and raw provider or account metadata.

Allowed: high-level hardening statements (non-root, read-only filesystem,
dropped capabilities, browser crawling OFF), current policy caps, exact test
counts with their commands, repository commit SHAs, measured attempt counts,
and evidence limitations.

Removing text from current files does not remove it from Git history or Issue
#1. Treat anything ever published as exposed, and never claim otherwise.

## File ownership and change rules

| File | Role | Change rule |
| --- | --- | --- |
| START_HERE.md | Universal bootstrap and read order | Jon approval |
| AI_SUPERVISOR.md | Governance | Jon approval |
| ROADMAP.md | Authoritative Stage 0–12 roadmap | Supervisor drafts; Jon approval |
| ARCHITECTURE_RESILIENCE.md | Accepted architecture foundation | Supervisor drafts; Jon approval |
| DECISIONS.md | Binding decisions and standing constraints | Supervisor drafts; Jon approval |
| CURRENT_TASK.md | The one active task | Executor updates status and progress, never scope |
| APPROVAL_QUEUE.md | Approval requests and decisions | Any agent may add requests; only Jon decides |
| CODEX_REPORT.md | Current execution evidence (legacy filename) | Any authorized executor, truthfully |
| README.md | Short human navigation | Keep consistent with START_HERE.md |
| history/README.md | Sanitized milestone index; never authority | Executor appends sanitized entries |

Historical files, Git history, and historical or agent-authored Issue #1
records are evidence and context, not execution authority. Direct durable Jon
decisions are authority, as defined above. Keep Issue #1 open; do not create a replacement.
