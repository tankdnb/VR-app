# GitHub Research Wave 92 Backlog

- Date: `2026-04-21`
- Scope: next GitHub discovery wave focused on
  `VRChat world persistence`, `inventory helpers`, `save-manager companions`,
  and `external-data bridges`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for VRChat persistence, inventory, and external-data helper repositories
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning in-world persistence, out-of-world save managers, holster inventory, and helper-process data bridges

## Work package B: Local source acquisition

- `Done` Confirm `NUSaveState` in local cache
- `Done` Confirm `ToNSaveManager` in local cache
- `Done` Confirm `InventorySystem` in local cache
- `Done` Confirm `Udon-MIDI-Web-Helper` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect avatar-slot application, build callbacks, and avatar-driven data flow in `NUSaveState`
- `Done` Inspect log watching, local data model, WebSocket API, and JS plugin host in `ToNSaveManager`
- `Done` Inspect automatic pickup registration, per-item ownership sync, and holster access gating in `InventorySystem`
- `Done` Inspect helper-process protocol, MIDI transport, and world-side bridge API in `Udon-MIDI-Web-Helper`

## Work package D: Repository updates

- `Done` Add Wave 92 plan document
- `Done` Add Wave 92 backlog document
- `Done` Add Wave 92 synthesis document
- `Done` Update the project registry for creator-world persistence and external-data bridge donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new persistence and transport patterns
- `Done` Update documentation indexes to include Wave 92

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `ToNSaveManager` through its script plugin surface and event model if a future pass needs a stronger `world companion automation host`
- `Next` Revisit `Udon-MIDI-Web-Helper` through local-storage and WebSocket edge cases if a future pass needs a stronger `external bridge threat model`
- `Next` Compare `NUSaveState` and `InventorySystem` whenever future work needs clearer `in-world ownership and persistence encoding` references
