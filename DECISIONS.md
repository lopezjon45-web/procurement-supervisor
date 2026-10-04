# Decisions

Binding decisions and standing constraints in force now. Superseded decisions
are not repeated here; see [history/README.md](history/README.md) and Git
history. Governance and roles are in [AI_SUPERVISOR.md](AI_SUPERVISOR.md).

## Product and operating direction

- Build universal procurement intelligence for AI agents with explicit
  evidence, provenance, and unknowns. Discovery leads are not verified product
  facts; compatibility needs evidence.
- [ROADMAP.md](ROADMAP.md) is the authoritative long-term navigation map.
  Every task names the roadmap stage it advances.
- [ARCHITECTURE_RESILIENCE.md](ARCHITECTURE_RESILIENCE.md) is the accepted
  Stage 0 foundation. AQ-009 Stage 0 is accepted and closed.
- The laptop-hosted pilot remains the operating direction. Cloud migration and
  broad publication require explicit approval and demonstrated value.

## Evidence invariants

The evidence invariants in [AI_SUPERVISOR.md](AI_SUPERVISOR.md) are binding.
External providers supply input or transport; they never own procurement truth.

## Standing constraints

Authority:

- One active task at a time.
- Approval of one gate never transfers to another gate or task.
- Capability does not imply authorization, and holding a credential does not
  authorize using a provider.
- No schema/migration, dependency, auth/authz, SourcePolicy, production,
  registry, billing, cloud, destructive, real-provider, or live-database action
  without the gate in AI_SUPERVISOR.md.

Discovery and quota:

- `max_queries=1` in the active provider discovery path.
- No automatic provider retry.
- Cache-first behavior. A cache read never silently triggers external
  discovery.
- Truthful `external_discovery_requests_attempted` accounting: every attempted
  request is counted, even on failure.
- Keep an approximately 25-search provider reserve. Unknown or unsafe provider
  allowance fails closed.
- Lifetime pilot caps, as last recorded: owner = 10, tester = 5. They are
  lifetime caps, not periodic resets, and unresolved holds do not expire
  automatically. The cap applied to the tester identity issued in the AQ-008
  rotation is not independently confirmed (see APPROVAL_QUEUE.md).
- Provider credential activation or use requires explicit approval.
  Credentials never enter source code, this repository, Issue #1, or logs. The
  secret-delivery mechanism is separately designed and approval-gated.

Runtime and data:

- Browser crawling OFF in production.
- Preserve exact source URLs, original timestamps, and SourcePolicy limits.
- Preserve historical evidence where policy permits. Destructive cache
  clearing is not the normal upgrade path.

## Cross-cutting future gates

Both are approved as permanent direction. Neither is approved for
installation or implementation.

### Universal Agent Governance Harness

Governance is vendor-neutral. Canonical truth lives in plain, versioned files
and recorded supervisor state, with no hidden model memory required. Every
agent bootstraps from [START_HERE.md](START_HERE.md). Vendor-specific files
(`AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, Cursor rules) are adapters, never
authority. Capability and authorization are checked separately; missing,
stale, inconsistent, or unverifiable authority fails closed. Deterministic
preflight and guard scripts should supplement prose. After every completed
gate, reconcile without rewriting history and verify the remote SHA, changed
files, and contents before advancing.

Installing the harness (adapters, guard scripts, vendor files) needs its own
reviewed merge/collision plan and Jon's approval. START_HERE.md as a
documentation file is not harness installation.

### Secure Agent Handshake

Required before broad public agent access, regardless of roadmap stage. The
design must provide:

- TLS transport;
- asymmetric proof of key possession, or an equivalently strong standard
  proof-of-possession mechanism;
- a server-generated, short-lived, single-use nonce/challenge with replay
  protection;
- protocol/security-version binding and downgrade resistance;
- short-lived sessions, sender-bound or proof-of-possession where practical;
- revocation and key rotation;
- safe handshake audit records;
- strict separation of authentication and authorization.

The handshake never exposes or transmits long-lived private keys; master,
database, or provider credentials; internal refresh-fencing capabilities; or
internal owner capability/token material. Every authentication adapter
resolves to the same internal Principal / authorization boundary. Static
bearer authentication may remain a bounded pilot mechanism only. Design and
implementation need separate approval.

## Provenance

These decisions were recorded from Jon's instructions in agent sessions. Most
have no direct durable Jon source; their provenance is "historical approval
reported; direct durable source unavailable". A Jon ratification comment on
Issue #1 is the proposed direct source.
