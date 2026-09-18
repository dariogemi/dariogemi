# Multi-Provider TTS Fallback

## Problem

Spoken announcements in an automated environment fail in annoying ways: a provider outage causes silence, while naive retry logic causes triple announcements. Caching makes it worse — a cached success looks identical to a fresh one if success is measured only by provider timestamps.

## Context

Lab need: a single speech-delivery entry point used by many automations, resilient across cloud and local synthesis providers, with exactly-once delivery perception.

## Approach

Built one router with a fixed provider order (primary cloud → secondary cloud → tertiary cloud → fully local engine) and automatic fallback on synthesis failure. The key design decision: **success is verified by real playback observation, not by provider timestamps alone** — so cached deliveries don't trigger false FAIL verdicts and repeated announcements.

## Architecture

```
text → TTS router → provider 1 ──synthesis ok + playback observed──→ done
                       │──fail──→ provider 2 ──→ provider 3 ──→ local engine
                       └── kill-switch per provider (e.g. zero-balance → skip immediately)
```

Delivery queueing prevents overlapping announcements; per-provider enable flags allow cost/availability control.

## Engineering considerations

* **Verify the effect, not the call** — playback observation beats timestamp comparison under caching.
* **Ordered degradation** — cloud quality first, local availability last; the system degrades gracefully instead of failing.
* **Cost-awareness** — a provider known to be out of credit is skipped without attempting.
* **Single contract** — callers pass text plus destination; all resilience lives inside the router.

## What it demonstrates

Fallback-chain design, verification thinking (observing outcomes vs. trusting API responses), graceful degradation, and cost-aware routing.

## Limitations / What this does NOT claim

* No latency benchmarks or audio-quality comparisons are published.
* Provider lineup is described as a pattern (cloud → cloud → local), not as an endorsement.
* Announcement contents and schedules are private and not reproduced.

## Evidence source

[EVIDENCE: REPO] Versioned router with documented failure-driven fixes (timestamp-vs-playback correction, credit-aware bypass). No provider credentials, message texts, or device identities reproduced.
