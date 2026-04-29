# GitHub Research Wave 102 Backlog

- Date: `2026-04-30`
- Scope: next GitHub discovery wave focused on
  `VRChat avatar emulation`, `gesture preview`, `repair`, and
  `OSC-assisted posing`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for avatar emulators, gesture preview tools, repair
  suites, and OSC-assisted pose systems
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning emulation, radial preview,
  manual-repair tooling, and OSC-sidecar posing

## Work package B: Local source acquisition

- `Done` Confirm `Av3Emulator` in local cache
- `Done` Confirm `VRC-Gesture-Manager` in local cache
- `Done` Confirm `avautils` in local cache
- `Done` Confirm `LexisPosingSystem` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect clone creation, expression menu, OSC loopback, and playable
  flow in `Av3Emulator`
- `Done` Inspect radial-menu preview, debug modules, OSC module, and dummy
  avatar modes in `VRC-Gesture-Manager`
- `Done` Inspect mesh combiner, bone remapper, and fitting-room utility layers
  in `avautils`
- `Done` Inspect the public OSC sidecar, save history, autosave, and scene
  orchestration flow in `LexisPosingSystem`

## Work package D: Repository updates

- `Done` Add Wave 102 plan document
- `Done` Add Wave 102 backlog document
- `Done` Add Wave 102 synthesis document
- `Done` Update the project registry for avatar preview and repair donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new emulation, repair, and OSC-sidecar
  patterns
- `Done` Update documentation indexes to include Wave 102

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Done` Commit the wave results
- `Done` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `LexisPosingSystem`
  only if a future pass has access to more of the closed Unity-side core or
  needs a deeper OSC-pose-automation comparison
- `Next` Compare `Av3Emulator` and `VRC-Gesture-Manager`
  whenever `VR-apps-lab` needs a sharper split between
  `full playable emulator`
  and
  `editor preview harness`
