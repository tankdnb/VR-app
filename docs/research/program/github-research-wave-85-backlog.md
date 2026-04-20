# GitHub Research Wave 85 Backlog

- Date: `2026-04-20`
- Scope: next GitHub discovery wave focused on
  `engine-side stereo panoramic viewers`, `vendor player samples`, and
  `layout-specific video surfaces`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for Unity and Unreal panoramic players plus vendor XR video samples
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning reusable Unity components, layout-specific vendor scenes, and an Unreal panoramic demo client

## Work package B: Local source acquisition

- `Done` Confirm `Unity_Panorama180View` in local cache
- `Done` Confirm `VideoPlayer-UnityXR` in local cache
- `Done` Confirm `ue5-stereo-panoramic-player-demo` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect projection enum, shader path, and image-video parity in `Unity_Panorama180View`
- `Done` Inspect scene layout split and material references in `VideoPlayer-UnityXR`
- `Done` Inspect product split and public demo surface in `ue5-stereo-panoramic-player-demo`

## Work package D: Repository updates

- `Done` Add Wave 85 plan document
- `Done` Add Wave 85 backlog document
- `Done` Add Wave 85 synthesis document
- `Done` Update the project registry for panoramic viewer and vendor playback references
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new engine-side immersive video patterns
- `Done` Update documentation indexes to include Wave 85

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `Unity_Panorama180View` visible as a compact `sphere plus projection mode` donor
- `Next` Keep `VideoPlayer-UnityXR` visible as a useful `vendor layout matrix` reference rather than a generic player framework
- `Next` Revisit `ue5-stereo-panoramic-player-demo` only when a future pass needs a tighter map of the external panoramic-player plugin boundary
