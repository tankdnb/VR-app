# GitHub Research Wave 79 Backlog

- Date: `2026-04-20`
- Scope: next GitHub discovery wave focused on
  `desktop-window overlay shells`, `Linux capture utilities`, and
  `launcher stubs`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for desktop capture overlays, Linux capture shells, and small launcher repos
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans a Unity desktop overlay, a Linux CLI capture host, and a thin launcher placeholder

## Work package B: Local source acquisition

- `Done` Confirm `DesktopOverlayer` in local cache
- `Done` Confirm `ovr-penguin` in local cache
- `Done` Confirm `RobloxVRLauncher` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect native texture grabber bridge and overlay transform controls in `DesktopOverlayer`
- `Done` Inspect command model, screen-capture flow, and OpenVR scene ownership in `ovr-penguin`
- `Done` Inspect the public snapshot of `RobloxVRLauncher` and classify it honestly as a thin launcher placeholder with no commits yet

## Work package D: Repository updates

- `Done` Add Wave 79 plan document
- `Done` Add Wave 79 backlog document
- `Done` Add Wave 79 synthesis document
- `Done` Update the project registry for desktop-window overlay shells and launcher stubs
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new capture-shell patterns
- `Done` Update documentation indexes to include Wave 79

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `DesktopOverlayer` visible as a useful `native texture to overlay surface` reference
- `Next` Keep `ovr-penguin` visible as a strong `CLI-first Linux overlay host` donor
- `Next` Keep `RobloxVRLauncher` tracked only as a `public placeholder` until real source appears
