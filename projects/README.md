# Engineering Case Studies

Sanitized, pattern-level write-ups distilled from versioned lab work. Each one states its problem, approach, architecture, engineering considerations, what it demonstrates, and — explicitly — what it does **not** claim. Nothing here exposes private infrastructure: no addresses, identifiers, credentials, or household information.

| Case study | Problem | Technologies & ideas | Professional skills shown |
|---|---|---|---|
| [Resilient multi-provider LLM routing](resilient-llm-router.md) | Single LLM provider = single point of failure | Error classification, fallback policy, circuit breaker, correlation IDs | AI orchestration, resilience design |
| [Idempotent AI coordination (BEACON)](beacon-coordination.md) | Duplicate or untraceable AI-driven actions | Lifecycle state machine, idempotency keys, durable records | Distributed coordination, auditability |
| [Multi-provider TTS fallback](tts-fallback-router.md) | Silent or repeated announcements on failure | Ordered fallback, real-playback verification | Fallback design, verification thinking |
| [Safety-constrained HVAC automation](hvac-safety-architecture.md) | Unsafe or wasteful autonomous actuation | Guardrailed actuation, occupancy policy, energy model | Control policy, specification writing |
| [Proprietary protocol research (CK99)](ck99-protocol-research.md) | Undocumented Bluetooth control protocol | Evidence-tagged RE, listen-first harness, safe bridge | Reverse engineering, hardware safety |
| [Edge observability & caretaker](edge-observability-caretaker.md) | Silent degradation on a constrained host | Layered detection, L1/L2/L3 risk classification, runbooks | SRE, incident response |
| [Local-first IoT migrations](local-first-iot-migrations.md) | Cloud dependence for local devices | Multi-evidence identity, staged migration, rollback points | Migration planning, validation rigor |

**Relevance for hiring:** the through-line is the same one that runs through 20 years of banking/payments work — contracts first, identity and traceability built in, failure modes explicit, changes reversible. See `../docs/evidence-map.md` for the claim-to-source ledger.
