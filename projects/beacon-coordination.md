# Idempotent AI Coordination (BEACON)

## Problem

Once AI components can trigger actions, two failure shapes appear: the same event processed twice (duplicate side effects) and results nobody can reconstruct after the fact (who decided what, from which evidence, under which delegation).

## Context

Lab work extending the LLM router: a coordination layer was needed so AI-driven responses to events would be traceable, non-duplicating, and auditable — without reimplementing routing or notification primitives.

## Approach

Designed BEACON as a thin coordination layer (not a mega-script): it owns event lifecycle and delegates execution. Every event gets a deterministic ID, every delegation an idempotency key, and every accepted result a durable structured record linking correlation → decision → evidence → timestamp.

## Architecture

```
event → BEACON (IDLE → NEW → IN_PROGRESS → VALIDATING → COMPLETED / FAILED / EXPIRED)
           │                    │
           │                    └── delegates to: router (reasoning), notifiers (delivery)
           └── durable records: ACCEPTED (correlation, result, provider, error class, timestamp)
```

BEACON reuses existing primitives (router, notification, observability) and adds only lifecycle, identity, and durability.

## Engineering considerations

* **Deterministic identity** — event IDs derived from source/reason/since; idempotency keys derived from event plus attempt.
* **Explicit states** — including UNCERTAIN and EXPIRED, so ambiguous outcomes are visible instead of silent.
* **Reconstructibility** — any ACCEPTED record can be walked back to its evidence.
* **No duplication of responsibilities** — BEACON never duplicates what the router or notifiers already own.

## What it demonstrates

Distributed coordination thinking: idempotency, lifecycle modeling, separation of concerns, and auditability — the same concepts behind payment traceability (STAN/RRN, reconciliation), applied to AI orchestration.

## Limitations / What this does NOT claim

* Not a multi-agent swarm or consensus protocol.
* No production-scale throughput claims.
* Coordination semantics only; domain actions stay in the delegated components.

## Evidence source

[EVIDENCE: REPO] Versioned coordination package plus handoff documentation written for future maintainers (human or AI). No event contents, entity identities, or household routines reproduced.
