# GitHub Research Wave 84 Backlog

- Date: `2026-04-20`
- Scope: next GitHub discovery wave focused on
  `browser panoramic video players`, `mobile wrappers`, and
  `projection-aware web playback plugins`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for browser panoramic players, Video.js VR plugins, and mobile 360 wrappers
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning browser-first players, player plugins, and thin native wrapper bridges

## Work package B: Local source acquisition

- `Done` Confirm `360WebPlayer` in local cache
- `Done` Confirm `videojs-panorama` in local cache
- `Done` Confirm `videojs-vr` in local cache
- `Done` Confirm `VR-Player` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect media, projection, stereoscopy, and renderer split in `360WebPlayer`
- `Done` Inspect canvas, hotspot, and video-type handling in `videojs-panorama`
- `Done` Inspect projection model and plugin lifecycle in `videojs-vr`
- `Done` Inspect Flutter-to-native bridge boundaries in `VR-Player`

## Work package D: Repository updates

- `Done` Add Wave 84 plan document
- `Done` Add Wave 84 backlog document
- `Done` Add Wave 84 synthesis document
- `Done` Update the project registry for browser and mobile panoramic playback donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new projection-aware playback patterns
- `Done` Update documentation indexes to include Wave 84

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `360WebPlayer` visible as a stronger `projection-aware browser playback framework` donor than the earlier shell-oriented media nodes
- `Next` Keep `videojs-panorama` and `videojs-vr` visible as reusable `existing-player enhancement` patterns
- `Next` Revisit `VR-Player` only when a future pass needs deeper `mobile wrapper over native XR playback SDK` comparisons
