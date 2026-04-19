# GitHub Research Wave 37 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `mixed-VR controller bridges`,
  `driver-side input emulation`, and `hand-tracking to controller adaptation`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for mixed-VR controller drivers, OpenHMD bridges, IPC driver bridges, and hand-tracking controller emulators
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans mature mixed-runtime bridges, an IPC-first driver bridge, and a hand-tracking controller-emulation repo
- `Done` Keep `PSVR-SteamVR-openHMD` as a comparison node instead of diluting the mainline shortlist

## Work package B: Local source acquisition

- `Done` Confirm `Oculus_Touch_Steam_Link` in local cache
- `Done` Confirm `SteamVR-OpenHMD` in local cache
- `Done` Confirm `Yet-Another-OpenVR-IPC-Driver` in local cache
- `Done` Confirm `Quest-Link-Hand-Tracking` in local cache
- `Done` Confirm comparison metadata for `PSVR-SteamVR-openHMD`
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect controller-role, render-model, and dual controller-or-tracker behavior in `Oculus_Touch_Steam_Link`
- `Done` Inspect device-selection config and OpenHMD-to-SteamVR bridge logic in `SteamVR-OpenHMD`
- `Done` Inspect IPC server, synthetic-device creation, and controller-state commands in `Yet-Another-OpenVR-IPC-Driver`
- `Done` Inspect public gesture-config and input-profile surfaces in `Quest-Link-Hand-Tracking`, and record the source-light caveat honestly

## Work package D: Repository updates

- `Done` Add Wave 37 plan document
- `Done` Add Wave 37 backlog document
- `Done` Add Wave 37 synthesis document
- `Done` Update the project registry for the strengthened mixed-VR bridge donors
- `Done` Update overlap families for controller bridges and hand-to-controller emulation
- `Done` Update `not-yet-studied-deeply.md` with the honest thin-source follow-up nodes
- `Done` Update the methods catalog with controller-emulation methods
- `Done` Update documentation indexes to include Wave 37

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `Quest-Link-Hand-Tracking` only if the public driver source grows beyond the current thin placeholder snapshot
- `Next` Revisit `PSVR-SteamVR-openHMD` if a future mixed-VR bridge wave needs a Linux and PSVR-specific comparison node
- `Next` Compare `Oculus_Touch_Steam_Link`, `SteamVR-OpenHMD`, `Yet-Another-OpenVR-IPC-Driver`, and `Quest-Link-Hand-Tracking` directly as `mixed-runtime bridge`, `OpenHMD hardware bridge`, `generic IPC controller bridge`, and `gesture-configurable hand emulation`
