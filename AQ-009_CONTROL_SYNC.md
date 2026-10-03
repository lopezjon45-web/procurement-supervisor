# AQ-009 control sync

**NON-AUTHORITATIVE HISTORICAL REFERENCE.** Nothing in this file authorizes
current work. Current state is in the files listed in
[START_HERE.md](START_HERE.md). The original, longer version of this file
remains in Git history (commit `df64791`), which, like Issue #1, is public and
unchanged.

## What this records

On 2026-09-28 Jon's instruction titled "Codex Execution Prompt — AQ-009
Architecture Resilience Baseline" was recorded, along with a supplied handoff
completing AQ-008. No direct durable source for that instruction or handoff
exists: historical approval reported; direct durable source unavailable.

## AQ-008 — completed / supervisor-reviewed (as supplied)

- An earlier attempt had stopped on a tester credential mismatch.
- The handoff reports that the tester credential was later rotated under
  Jon's approval. That rotation has no direct durable source; see
  AQ008-ROTATION-PROVENANCE in [APPROVAL_QUEUE.md](APPROVAL_QUEUE.md).
- An independent outside agent made exactly one cache-only
  `search_procurement_intelligence` call (replacement charger, MacBook Air,
  A2681, both refresh flags false). Result: STALE, five DISCOVERED leads,
  compatibility and freshness unknown, zero external discovery attempts.
- Reported server-side counts: one tester call, no other tool calls, no
  discovery-budget reservations or settlements. The usage row's
  `verification_fetches` was NULL (not measured), not zero.
- Feedback: the response structure was understandable, but the stale leads were
  not actionable and included clearly irrelevant sources.

## Why it mattered

The AQ-008 feedback showed that discovery relevance and cache quality were the
main gap. That motivated AQ-009, which established the Stage 0 architecture
resilience foundation ([ROADMAP.md](ROADMAP.md),
[ARCHITECTURE_RESILIENCE.md](ARCHITECTURE_RESILIENCE.md)). Jon later accepted
and closed Stage 0, and AQ-010 began Stage 1 cache/relevance work.
