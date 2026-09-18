# Safety-Constrained HVAC Automation

## Problem

Environmental automation that actuates directly on sensor readings can produce unsafe or wasteful outcomes: extreme setpoints, heating an empty space, or fighting occupant intent. Comfort, energy cost, and safety compete, and naive rules optimize only the first.

## Context

Lab work on climate supervision: design the control policy and safety envelope **before** automating actuation, with energy-cost awareness for a time-of-use tariff environment.

## Approach

Separated the problem into models (device, thermal, occupancy, energy, environment, learning) plus explicit control and safety policies, then implemented a lightweight guardian: setpoints are capped within a band around measured temperature, actuation is suppressed during sleep/absence conditions, prolonged consumption without interaction triggers shutoff, and manual holds expire automatically.

## Architecture

```
telemetry (temp, power, occupancy) → policy engine → guarded actuation
        │                                  │
        └── energy model (tariff-aware) ────┘
safety envelope: setpoint band, sleep suppression, consumption watchdog, hold expiry
```

A full supervisor specification (control policy, safety policy, entity map, implementation plan, incident analysis) backs the implementation.

## Engineering considerations

* **Guardrails on actuation, not just triggers** — the policy constrains what automation is allowed to do, not only when it fires.
* **Occupancy as a first-class signal** — empty-space conditioning is treated as waste by default.
* **Holds must expire** — any manual override returns to policy automatically.
* **Tariff-awareness** — energy cost modeling informs when conditioning is worth running.

## What it demonstrates

Control-system thinking: safety envelopes, policy/actuation separation, energy modeling, and BA-style specification writing (MASTER_SPEC, CONTROL_POLICY, SAFETY_POLICY, incident runbook).

## Limitations / What this does NOT claim

* No predictive ML or learned thermal model in production; learning model is specified, not deployed.
* No published savings percentages or comfort metrics.
* Single-zone scope; not a whole-building BMS.

## Evidence source

[EVIDENCE: REPO] Guardian implementation plus a 13-document supervisor specification set and an executed/aborted controlled A/C test with written decision record. No device identities, locations, schedules, or tariff account details reproduced.
