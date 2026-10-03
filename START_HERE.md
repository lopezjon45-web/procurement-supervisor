# Start here

The universal bootstrap for any person or agent working in this repository.
It does not depend on a particular vendor, model, or hidden memory: everything
needed to act is in the versioned files listed below.

## What this repository is

The public control plane for the procurement intelligence project. It holds
governance, binding decisions, the single active task, approval requests,
execution evidence, and the long-term roadmap. Product code and private
operational material live elsewhere and are never published here.

## Read in this order

1. START_HERE.md: this file.
2. [AI_SUPERVISOR.md](AI_SUPERVISOR.md): governance, roles, approval gates, evidence and publication rules.
3. [DECISIONS.md](DECISIONS.md): binding decisions and standing constraints.
4. [CURRENT_TASK.md](CURRENT_TASK.md): the one active task and its stop boundary.
5. [APPROVAL_QUEUE.md](APPROVAL_QUEUE.md): approval requests and Jon's decisions.
6. [CODEX_REPORT.md](CODEX_REPORT.md): current execution evidence and open risks.
7. [ROADMAP.md](ROADMAP.md): the authoritative Stage 0–12 roadmap and cross-cutting gates.
8. [ARCHITECTURE_RESILIENCE.md](ARCHITECTURE_RESILIENCE.md): authority, dependency, and failure model.
9. Only if needed: [history/README.md](history/README.md), Git history, and
   [Supervisor Issue #1](https://github.com/lopezjon45-web/procurement-supervisor/issues/1).

## Rules that apply before anything else

- Authority order:
  1. Jon's latest direct durable decision (see AI_SUPERVISOR.md) is the
     highest authority.
  2. The current control files come next. If they have not yet been
     reconciled to Jon's latest decision, stop `BLOCKED` until they are.
  3. Historical summaries, Git history, older or agent-authored Issue #1
     comments, and any agent's memory are evidence only, never authority.
- Historical records never authorize current execution.
- Missing, stale, or inconsistent authority means stop `BLOCKED` and state
  what is missing.
- Capability is not authorization. Holding a credential, tool access, or push
  rights never means you may use them.
- AUTHENTICATED != AUTHORIZED.
- Exactly one active task at a time. Approval of one gate never carries over
  to another.
- No hidden model memory is required or trusted. If it is not in these files
  or a linked durable record, treat it as unknown.
- Vendor-specific agent files (for example `AGENTS.md`, `CLAUDE.md`,
  `GEMINI.md`, Cursor rules) are adapters only. They may point here; they
  never override these files.
- After every completed gate, publish without rewriting history, then verify
  the remote commit SHA, the exact changed files, and the remote file contents
  before advancing.
- This repository is public. Follow the public information boundary in
  AI_SUPERVISOR.md.

Every work cycle ends in exactly one of `CONTINUE`, `APPROVAL_REQUIRED`, or
`BLOCKED`, as defined in AI_SUPERVISOR.md.

This file is a documentation-only bootstrap. It is not the Universal Agent
Governance Harness; installing the harness (adapters, guard scripts, vendor
files) remains separately approval-gated.
