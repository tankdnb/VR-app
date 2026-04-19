# GitHub Research Wave 57 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `Linux overlay control shells`, `desktop-service panels`, and
  `interaction variants`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for Linux overlay shells, Qt dashboard panels, and `X11`-oriented SteamVR tools
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans screen-control overlays, desktop-service panels, and audio-routing dashboards

## Work package B: Local source acquisition

- `Done` Confirm `OVR4X11` in local cache
- `Done` Confirm `SVRLinuxTools` in local cache
- `Done` Confirm `OpenVR_Audio_Manager` in local cache
- `Done` Confirm `sinpin-vr` as a surfaced comparison node
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect `X11` capture, keyboard input, and controller-pointer logic in `OVR4X11`
- `Done` Inspect Qt panel host, `--novr` path, and service-control structure in `SVRLinuxTools`
- `Done` Inspect overlay shell, audio-device state model, and HMD-aware switching logic in `OpenVR_Audio_Manager`
- `Done` Confirm that `sinpin-vr` is a GitHub relocation stub rather than a mainline code donor

## Work package D: Repository updates

- `Done` Add Wave 57 plan document
- `Done` Add Wave 57 backlog document
- `Done` Add Wave 57 synthesis document
- `Done` Update the project registry for Linux overlay control-shell donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes where needed
- `Done` Update the methods catalog with Linux control-shell methods
- `Done` Update documentation indexes to include Wave 57

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `OVR4X11` visible whenever a future branch needs a `desktop capture plus controller-mouse overlay shell`
- `Next` Keep `SVRLinuxTools` visible whenever a future branch needs a `desktop-service panel with a non-VR debug path`
- `Next` Revisit `sinpin-vr` only if the moved upstream becomes relevant enough to justify a non-GitHub recovery pass
