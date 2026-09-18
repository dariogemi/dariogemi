# Proprietary Protocol Research (LG XBOOM CK99)

## Problem

A Bluetooth audio system (LG XBOOM CK99) had no supported integration path for automation: control flowed through a vendor mobile app over an undocumented proprietary protocol. Any automation required understanding the wire protocol first — without breaking the device.

## Context

Independent lab research: determine whether safe, read-only-leaning integration was feasible, and document the protocol honestly with evidence grades.

## Approach

Three phases: (1) **offline analysis** — decompiled the vendor app, identified the transport (Bluetooth Classic RFCOMM/SPP with ASCII-framed proprietary frames and a checksum) vs. the BLE channel (used only for speaker grouping, not control), classified the device family, and mapped candidate commands from code strings and the official manual; (2) **evidence-tagged documentation** — every claim tagged VERIFIED (seen in artifacts), HYPOTHESIS (reasonable, unconfirmed), or UNKNOWN (needs hardware test); (3) **listen-first field harness** — a stdlib-only investigator that passively captures first, sends only a tiny allowlist of query-shaped frames guarded by byte-level shape checks, blacklists destabilizing queries, and uses backoff plus disk guards.

A controller-side wrapper coordinates power intent over MQTT plus IR without ever issuing raw protocol writes.

## Architecture

```
offline: APK + manual → frame format + command map (tagged V/H/?)
field:   SPP listener → capture → allowlisted queries only → structured evidence
control: intent → MQTT topic → bridge + IR actuation (no raw writes from HA)
```

## Engineering considerations

* **Evidence tags as method** — separating verified facts from hypotheses is the deliverable, not just the protocol map.
* **Safety by construction** — listen-first, shape-guarded queries, blacklisting, backoff, disk guards, graceful shutdown.
* **No-write default** — the control wrapper deliberately cannot emit protocol writes.
* **Portability** — stdlib-only harness runs on any Bluetooth-capable Linux host, not tied to one container.

## What it demonstrates

Methodical reverse engineering, hardware safety discipline, protocol analysis (framing, checksums, transport separation), and honest technical writing under uncertainty.

## Limitations / What this does NOT claim

* Phase-1 document is explicitly a working draft; runtime behavior was unverified at time of writing.
* Full control (volume/EQ/lighting/effects) is NOT claimed as verified — only mapped as candidates.
* The successor vendor app was not analyzed.

## Evidence source

[EVIDENCE: REPO] ~900-line evidence-tagged research document, autonomous investigator harness with README, overnight field report, and bridge documentation. No MAC addresses, RF channels, raw frames, keys, or pairing details reproduced.
