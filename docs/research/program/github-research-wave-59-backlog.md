# GitHub Research Wave 59 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `embodied locomotion overlays`, `live tuning surfaces`, and
  `external-device control panels`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for locomotion overlays, VR tuning tools, and external-device control panels
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans controllerless locomotion, desktop editor plus live overlay tuning, and remote-device control surfaces

## Work package B: Local source acquisition

- `Done` Confirm `bikeheadvr` in local cache
- `Done` Confirm `Omni-Tune` in local cache
- `Done` Confirm `OVR-Shock` in local cache
- `Done` Confirm `VROverlay` in local cache
- `Done` Confirm `PopExposeXr` as a surfaced comparison node
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect gaze buttons, pedal estimation, and OSC export path in `bikeheadvr`
- `Done` Inspect desktop editor, native helper protocol, and live overlay mirroring in `Omni-Tune`
- `Done` Inspect API client, persisted config, and hand-specific overlay UI in `OVR-Shock`
- `Done` Inspect older Unity overlay lineage and compare it against the newer `OVR-Shock` branch
- `Done` Confirm that `PopExposeXr` is too thin for mainline promotion in this pass

## Work package D: Repository updates

- `Done` Add Wave 59 plan document
- `Done` Add Wave 59 backlog document
- `Done` Add Wave 59 synthesis document
- `Done` Update the project registry for embodied-control and device-panel overlays
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes where needed
- `Done` Update the methods catalog with embodied-control and device-panel methods
- `Done` Update documentation indexes to include Wave 59

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `bikeheadvr` visible whenever a future branch needs `controllerless locomotion overlay plus avatar-facing output`
- `Next` Keep `Omni-Tune` visible whenever a future branch needs `desktop editor plus native VR helper` architecture
- `Next` Revisit `OpenShock/VROverlay` only if a future lineage pass needs a sharper comparison against `OVR-Shock`
