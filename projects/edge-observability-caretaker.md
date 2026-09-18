# Edge Observability & Autonomous Caretaker

## Problem

A resource-constrained edge host (single-board computer running home infrastructure: automation, video, voice, AI agents) degrades silently — memory pressure, thermal throttling, runaway add-ons, stale tokens — and each incident costs manual diagnosis. Full-time monitoring is disproportionate; zero monitoring is negligent.

## Context

Lab operations: keep a complex edge stack healthy with minimal human attention, while guaranteeing the automation never makes risky changes on its own.

## Approach

Built a layered maintenance system: **observe** (periodic snapshots of CPU, memory, temperature, disk, service states), **detect** (finding rules with known-good/known-false-positive lists), **classify risk** (L1 safe auto-fix / L2 needs approval / L3 report-only), and **report** (digest notifications, silent when clean). Backed by runbooks for every known incident class and shell/Python tooling for diagnosis.

## Architecture

```
observe → detect → classify (L1/L2/L3) → act or escalate → digest
   │                                        │
   └── sensors (cpu/temp/mem/disk/uptime)   └── runbooks per incident class
```

Cooldowns prevent alert storms; institutional memory (decisions file) prevents the system from re-litigating settled choices.

## Engineering considerations

* **Risk classification is the product** — the detect/diagnose part is easy; deciding what the machine may do alone is the engineering.
* **Read-only by default** — observation and detection never mutate; only classified-safe L1 actions execute.
* **Known-false-positive handling** — detection quality is managed explicitly, not assumed.
* **Memory of decisions** — settled operational choices are recorded so future troubleshooting (human or AI) doesn't regress them.

## What it demonstrates

SRE thinking for constrained environments, incident-response design, runbook culture, and autonomous-operation safety — directly transferable to enterprise service management (RACI/SLO practice from TCS/PwC work).

## Limitations / What this does NOT claim

* Not a replacement for enterprise monitoring stacks; scoped to a single edge host.
* L1 auto-fixes are narrow and safe by design; most novel findings route to human review.
* No uptime/SLA statistics are published.

## Evidence source

[EVIDENCE: REPO] Maintenance package plus memory-incident-response framework, diagnostic scripts, runbook set, and an architecture document. No host identifiers, network addresses, service credentials, or alert contents reproduced.
