# GitHub Research Wave 41 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `avatar-facing OSC companions`, `routing sidecars`, and
  `consumer automation utilities`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for VRChat OSC routers, consumer automation sidecars, and avatar-facing helpers
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans a broad Electron platform, a focused router, a plugin telemetry host, and several narrow desktop-action bridges
- `Done` Keep `VRCOSCUtils` as a weaker comparison node instead of replacing the stronger mainline donors

## Work package B: Local source acquisition

- `Done` Confirm `OscGoesBrrr` in local cache
- `Done` Confirm `VRCRouter` in local cache
- `Done` Confirm `Quest2-VRC` in local cache
- `Done` Confirm `VRCMeeter` in local cache
- `Done` Confirm `VRCAvatarParameterSync` in local cache
- `Done` Confirm `OSCLeash` in local cache
- `Done` Confirm `OSCLock` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect the typed IPC, service split, and diagnostics surfaces in `OscGoesBrrr`
- `Done` Inspect route presets, app lifecycle helpers, and VRChat gating in `VRCRouter`
- `Done` Inspect plugin loading, telemetry modules, and OSC fan-out in `Quest2-VRC`
- `Done` Inspect `OSCQuery`-aware Voicemeeter bridging in `VRCMeeter`
- `Done` Inspect avatar-parameter snapshot and replay behavior in `VRCAvatarParameterSync`
- `Done` Inspect config-driven locomotion behavior in `OSCLeash`
- `Done` Inspect timer-to-Bluetooth actuator flow in `OSCLock`

## Work package D: Repository updates

- `Done` Add Wave 41 plan document
- `Done` Add Wave 41 backlog document
- `Done` Add Wave 41 synthesis document
- `Done` Update the project registry for avatar-facing OSC companions and automation sidecars
- `Done` Update overlap families for routers, plugin telemetry hosts, and consumer-action bridges
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes
- `Done` Update the methods catalog with routing and automation-sidecar methods
- `Done` Update documentation indexes to include Wave 41

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `OscGoesBrrr` if a future pass needs a deeper platform-level comparison of its service surface, plugin envelope, or diagnostics views
- `Next` Compare `VRCRouter`, `VRCMeeter`, `VRCAvatarParameterSync`, and `OSCLock` directly as `router`, `desktop-action bridge`, `parameter persistence helper`, and `consumer actuator sidecar`
