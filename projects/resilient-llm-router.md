# Resilient Multi-Provider LLM Routing

## Problem

A conversational system backed by a single LLM provider inherits that provider's failure modes: quota exhaustion, authentication breaks, rate limits, network faults, and 5xx errors all become user-visible outages. Retrying blindly can amplify the problem (e.g. retrying quota errors) or mask it.

## Context

Applied-AI lab work (Nivora, 2022–Present): an always-on assistant layer needed provider resilience without coupling every caller to provider-specific error handling.

## Approach

Built a minimal central router: one entry point receives text plus context, attempts the primary provider, classifies any failure, and falls back to a secondary provider **only for failure classes where fallback is rational** (quota, network, timeout, 5xx). Non-retryable classes (authentication, bad request, content policy) short-circuit instead of burning fallback budget.

## Architecture

```
caller → router → primary provider ──success──→ result
                    │
                    └──failure → classify → retryable? ──yes──→ fallback provider → result
                                                     └──no───→ structured failure (no retry storm)
```

Supporting mechanisms: strict hop/retry budgets (single fallback hop, zero blind retries), a circuit breaker (closed/open/half-open) driven by failure class, per-call correlation IDs, and counters/timers feeding an observability layer.

## Engineering considerations

* **Failure classification before action** — the router's core value is the taxonomy, not the HTTP call.
* **Budgets as design** — hop and retry limits are load-bearing reliability features.
* **Correlation everywhere** — every delegation carries an ID so results are reconstructible later.
* **Separation of concerns** — no speech, vision, or tool-calling logic inside the router; it routes text and reports outcomes.

## What it demonstrates

Provider-resilient AI orchestration, failure-mode design, circuit breaking, correlation/idempotency thinking transferred from payments (where duplicate or untraceable transactions are unacceptable) into AI systems.

## Limitations / What this does NOT claim

* No RAG, fine-tuning, or formal eval harness is claimed.
* No measured SLOs or latency percentiles are published.
* Probes and canary checks are described as method, not as production traffic evidence.

## Evidence source

[EVIDENCE: REPO] Versioned lab implementation (router package with probes/canary/observability) plus incident-driven refinements in commit history. No provider credentials, prompts, network locations, or household context are reproduced here.
