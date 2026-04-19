# GitHub Research Wave 16 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `device-monitor overlays`,
  `battery watchers`, `pose-inspection exporters`, and
  `SteamVR environment-side helper tools`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for battery monitors, charging-state watchers, and device-health helpers
- `Done` Search GitHub for pose-inspection and device-export micro-tools
- `Done` Search GitHub for Linux-side SteamVR helper collections and daemons
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for the wave
- `Done` Record `Denwa/vive-wireless-info-overlay` as a source-light comparison node instead of over-promoting it

## Work package B: Local source acquisition

- `Done` Confirm `jangxx/openvr-battery-monitoring` in local cache
- `Done` Confirm `mutr/openvr_battery_monitor` in local cache
- `Done` Confirm `KaftanOS/SteamVR-Battery-Checker` in local cache
- `Done` Confirm `MuffinTastic/openvr-device-positions` in local cache
- `Done` Confirm `DavidRisch/steamvr_utils` in local cache
- `Done` Confirm `Denwa/vive-wireless-info-overlay` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect tray icon, mute list, and notification channels in `openvr-battery-monitoring`
- `Done` Inspect InfluxDB write path and SteamVR auto-start model in `openvr_battery_monitor`
- `Done` Inspect the one-shot OpenVR polling script in `SteamVR-Battery-Checker`
- `Done` Inspect overlay thread, pose collection, and FBX export flow in `openvr-device-positions`
- `Done` Inspect daemon staging, audio switching, and base-station control flow in `steamvr_utils`
- `Done` Inspect `vive-wireless-info-overlay` far enough to classify it as product-reference-first and source-light

## Work package D: Repository updates

- `Done` Add Wave 16 plan document
- `Done` Add Wave 16 backlog document
- `Done` Add Wave 16 synthesis document
- `Done` Update the project registry for the newly promoted monitor and helper repos
- `Done` Update overlap families for battery watchers, creator-side pose utilities, and SteamVR hygiene helpers
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-up nodes
- `Done` Update the methods catalog with new monitor and pose-export methods
- `Done` Update documentation indexes to include Wave 16

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Done` Commit the wave results
- `Done` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Compare `openvr-battery-monitoring`, `openvr_battery_monitor`, and `SteamVR-Battery-Checker` directly as one `state-transition alert vs metrics logger vs one-shot inspector` note
- `Next` Revisit `Denwa/vive-wireless-info-overlay` only if fuller source appears or a stronger implementation mirror is found
- `Next` Compare `openvr-device-positions` with `triad_openvr`, `openvr-metrics`, and creator-side capture tools as one `live runtime state -> exportable artifact` pattern
- `Next` Compare `steamvr_utils`, `steamvr-exconfig`, and `SteamVR-Toggle` as one `SteamVR environment hygiene helper` branch
