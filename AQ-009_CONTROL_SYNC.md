# AQ-009 Control Sync

## Later Stage 0 disposition

Jon's active instruction beginning “YES — I approve AQ-010 Slice 1A
implementation and tests” accepts and closes AQ-009 Stage 0 and makes AQ-010
the sole current Roadmap Stage 1 task. This later explicit decision supersedes
the pending foundation-review status below; the original AQ-009 publication
record and its evidence limitations remain historical. No durable
session-message URL was supplied.

## Source and evidence boundary

Recorded on 2026-09-28 from Jon's active instruction titled **“Codex Execution
Prompt — AQ-009 Architecture Resilience Baseline”**, including its three supplied
supervisor documents. No durable session-message URL or separate completion
evidence link was supplied. This file preserves that handoff's sanitized facts
and decisions; it is not a new database measurement or procurement test.

The GitHub baseline was commit
`0e933fc3c4f5936c17020f09b73e43d02d09c8b0`. Its
[AQ-008 credential-blocked packet](https://github.com/lopezjon45-web/procurement-supervisor/issues/1#issuecomment-5788351714)
describes an earlier attempt. Preserve that packet and all historical entries.
Its blocker is superseded by the later completion below, not treated as current.

## AQ-008 status to record

**AQ-008: COMPLETED / SUPERVISOR-REVIEWED**, as explicitly directed by Jon.
The supplied handoff records independent outside-agent and server-side evidence:

- Existing tester identity was rotated under Jon's explicit approval; owner identity and other configuration were preserved.
- New tester fingerprint: `eab3b2dd9edce7ae`.
- Independent outside agent on a phone connected to the public MCP endpoint.
- Exactly one `search_procurement_intelligence` call was made with the following arguments:

```json
{
  "query": "replacement charger",
  "device": "MacBook Air",
  "model": "A2681",
  "minimum_evidence": "discovered",
  "refresh_if_missing": false,
  "refresh_if_stale": false
}
```

`model_identifier` was omitted; it is not inferred or added.

- Result: **STALE**, five discovery leads, all **DISCOVERED**, compatibility/freshness unknown.
- `external_discovery_requests_attempted=0`; `external_discovery_invoked=false`.

Server-side Neon evidence reported for this completed tester identity/test scope:

| Measurement | Reported result |
| --- | --- |
| Total tester rows | 1 |
| `search_intel` / `search_procurement_intelligence` calls | 1 |
| Other tool calls | 0 |
| Measured external discovery | 0 |
| Discovery-budget reservations | 0 |
| Discovery-budget settlements | 0 |
| Individual usage row `verification_fetches` | **NULL / not measured** |

`verification_fetches` must not be represented as independently measured zero.
The earlier tester identity's historical rows and hold are not erased or reset
by these scoped counts. No new owner balances, timestamps, raw rows, lead URLs,
runtime/cleanup measurements, or provider allowance readings are supplied here;
do not infer them or reuse earlier readings as current evidence.

Outside-agent feedback: response structure was understandable, but the stale
cached leads were not actionable and included clearly irrelevant sources. The
primary exposed weakness was discovery relevance/cache quality. This qualitative
feedback does not verify product facts or compatibility, establish broad
usefulness, or supply a reuse-intent answer or numerical usefulness score.

No outside-agent client/model name is supplied for the completed phone test; do
not conflate it with the earlier blocked Claude Code preparation. The test was
not repeated and Neon was not queried during this documentation cycle.

## AQ-009 decision

Jon explicitly approved establishing a concrete architecture foundation that
remains coherent when optional external services disappear.

AQ-009 advances **[ROADMAP.md](ROADMAP.md) Stage 0**. Its scope is
documentation/control-plane architecture only:

- long-term [ROADMAP.md](ROADMAP.md);
- [ARCHITECTURE_RESILIENCE.md](ARCHITECTURE_RESILIENCE.md);
- authoritative-state model;
- dependency tiers;
- ports/adapters boundaries;
- capability/degraded-mode rules;
- liveness/readiness distinction;
- transaction idempotency/outbox principles;
- authentication abstraction;
- Redis-as-disposable-accelerator rule;
- mandatory failure-mode testing.

AQ-009 does **not** by itself approve:

- schema/migration creation or application, including migration 006;
- product-code changes;
- dependency additions;
- Redis deployment;
- authentication/authorization changes or credential rotation;
- production container or deployment changes;
- provider activation, SerpApi activity, external discovery, or procurement MCP test calls;
- source-policy changes;
- transaction execution or implementation;
- billing/payment changes;
- cache deletion or invalidation.

After foundation review, cache/relevance hardening is the first implementation
stage; it still requires separately scoped authorization.

## Publication and review gates

1. Prepare the documentation locally and show Jon the exact files, summaries,
   exclusions, and proposed commit message.
2. **STOP for Jon's YES before any commit or push.** Publication approval is
   separate from preparation approval; preparation does not satisfy this gate.
3. Only after YES: publish the approved documentation, post one sanitized handoff
   to the existing permanent [Supervisor Queue Issue #1](https://github.com/lopezjon45-web/procurement-supervisor/issues/1),
   and verify the resulting commit/files.
4. Finish **APPROVAL_REQUIRED** for supervisor review before any AQ-009
   implementation work begins. Jon remains the final YES / NO authority.

Publication approval does not by itself approve the architecture review outcome
or authorize product implementation.

## Publication decision recorded after review packet

Jon replied **“yes”** to the prepared eight-file change summary, exclusions,
proposed commit message, and one sanitized Issue #1 handoff in the active
session. No durable message URL was supplied. This explicit YES satisfies the
commit/push gate for this exact documentation scope only. Foundation review
remains pending, and no implementation is authorized.
