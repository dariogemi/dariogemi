# Local-First IoT Migrations

## Problem

Smart devices bound to vendor clouds inherit cloud failure modes — outages, latency, account changes, privacy exposure — for actions that are physically local (a switch next to its controller). Migrating to local control is risky when device identity is ambiguous: similar models, duplicate names, and stale references make it easy to migrate the wrong device.

## Context

Lab program: move a fleet of ~20 cloud-managed devices (plugs, switches, sensors across two vendor ecosystems) to local control without breaking automations, scenes, or dashboards.

## Approach

Staged, evidence-driven migration: (1) **inventory** every device from the vendor API (IDs, product, category, network behavior); (2) **validate locally** with port scans plus protocol-level DPS/state reads, correlating each physical device to its cloud record before touching configuration; (3) **map references** — every automation, script, scene, and dashboard reference catalogued per device; (4) **migrate in small batches** with git checkpoints before each batch and post-change verification (config parse, residual-reference search); (5) **never edit registries directly** — identity changes go through supported paths only, with documented rules for ambiguous cases (document-and-skip, never guess).

For one ecosystem, critical devices required ≥3 independent evidences (exact name uniqueness, model-family bijection, area, hardware-identifier continuity, functional-reference coherence) before migration.

## Architecture

```
inventory (cloud record) → local validation (protocol readback) → reference map
      → checkpoint → batch migration → verify (parse + residual search) → next batch
```

## Engineering considerations

* **Identity before action** — the migration's core artifact is the device map, not the config edit.
* **Batch size as risk control** — small batches with checkpoints bound the blast radius.
* **Ambiguity policy** — anything ambiguous is documented and skipped, never force-migrated.
* **Registry discipline** — platform-managed identity stores are never hand-edited.

## What it demonstrates

Migration planning, device/entity identity management, staged rollout with rollback points, and validation rigor — the same discipline as enterprise data or platform migrations.

## Limitations / What this does NOT claim

* Device counts and validation ratios are described as method illustration; the live inventory is private.
* No vendor endorsement or criticism is intended; local-first is presented as an architectural choice.
* Protocol specifics, keys, identifiers, and addresses are intentionally omitted.

## Evidence source

[EVIDENCE: REPO] Versioned migration workspace (inventory, device map, migration plan, backups) plus batch commits in history. No device IDs, keys, MACs, IP addresses, account identifiers, or network topology reproduced.
