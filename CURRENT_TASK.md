# Current task

```text
task: Stage 2 — Agent-Facing Procurement Contract (first slice)
roadmap_stage: 2
state: IN_PROGRESS (local implementation; nothing deployed)
```

Jon remains the final YES / NO authority.

## Operating note (2026-10-04)

Jon directed in the executing session that
[ARCHITECTURE_RESILIENCE.md](ARCHITECTURE_RESILIENCE.md) and
[ROADMAP.md](ROADMAP.md) are the standing authorities for product work, below
his direct instruction, and that the per-step approval queue is set aside for
now. The statuses below were approved by him in that session. They were
recorded by the executing agent; no direct durable Issue #1 record exists for
them yet.

Still decided by Jon each time: provider quota, any write or migration against
a live database, starting or replacing the public service, and publishing.

## Stage 1 — Cache and Relevance Integrity

| Item | Status |
| --- | --- |
| Slice 1A | COMPLETED / SUPERVISOR-REVIEWED |
| Slice 1B (refresh coordination) | IMPLEMENTED / ACCEPTED LOCALLY (merged to the product main branch) / NOT DEPLOYED |
| Migration 006 | CREATED / applied to throwaway test databases only / NOT APPLIED to any live database |
| Slice 1B isolated PostgreSQL validation | DONE on throwaway local databases |
| Readiness and failure-mode work | IMPLEMENTED / ACCEPTED LOCALLY / NOT DEPLOYED |
| Relevance screening version 4 | IMPLEMENTED / ACCEPTED LOCALLY / NOT DEPLOYED |
| Predeclared multi-query relevance set | RUN TWICE (ten queries each, 20 provider searches in total) |
| Live read-only migration-history preflight | NOT EXECUTED; superseded as a gate by the operating note, still unrun |

Evidence and limits are in [CODEX_REPORT.md](CODEX_REPORT.md).

Stage 1's roadmap conditions are met on local and throwaway-database evidence.
Stage 1 is **not deployed**: the running service predates all of this work.

## Open risks

- Nothing from Stage 1 has run against the live database or in the deployed
  service.
- Deploying screening version 4 changes the cache identity: earlier cached
  answers stay stored but are not reused.
- Relevance evidence is ten queries, seven of them written by the executing
  agent. It is not proof of broad quality.
- One query in the set returns no usable lead, for a reason not yet explained.
- Model-generation, product-variant, and seller judgments are not made by
  lexical screening; they belong to Stages 3 and 4.

## Next action

1. Stage 2, first slice: one front-door tool that returns options, evidence
   state, freshness, explicit unknowns, next actions, and current capabilities,
   without renaming or replacing an existing tool.
2. Jon decides when to deploy Stage 1 (live migration 006, new image, restart).
