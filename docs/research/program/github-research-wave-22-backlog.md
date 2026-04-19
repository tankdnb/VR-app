# GitHub Research Wave 22 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `vision tracking hosts`,
  `camera full-body bridges`, and `hand-input sidecar stacks`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Re-check the strongest `Partially studied` entries from the Wave 13 family
- `Done` Search lightly for maintained forks or stronger successors without letting the wave sprawl
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for repeat code-level inspection
- `Done` Record `chnoblouch/aethervr` and `MasonSakai/VR-AI-Full-Body-Tracking` as follow-up comparison nodes instead of core wave entries

## Work package B: Local source acquisition

- `Done` Confirm `KinectToVR/Amethyst` in local cache
- `Done` Confirm `KinectToVR/KinectToVR` in local cache
- `Done` Confirm `ju1ce/Mediapipe-VR-Fullbody-Tracking` in local cache
- `Done` Confirm `Wunder-Wulfe/NVIDIA-BodyTracking` in local cache
- `Done` Confirm `Nordskog/HandOfLesser` in local cache
- `Done` Confirm `NovaAshwolfDev/HandCameraDriver` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect plugin and service-endpoint architecture in `Amethyst`
- `Done` Inspect legacy multi-process and calibration-heavy architecture in `KinectToVR`
- `Done` Inspect backend switching and WebUI control surface in `Mediapipe-VR-Fullbody-Tracking`
- `Done` Inspect GPU-assisted tracking pipeline and overlay split in `NVIDIA-BodyTracking`
- `Done` Inspect packet transport, SteamVR output, and VRChat split in `HandOfLesser`
- `Done` Inspect the minimal sidecar-plus-driver shell in `HandCameraDriver`

## Work package D: Repository updates

- `Done` Add Wave 22 plan document
- `Done` Add Wave 22 backlog document
- `Done` Add Wave 22 synthesis document
- `Done` Update the project registry for the newly clarified vision-tracking repos
- `Done` Update overlap families for the vision and hand-input family
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new tracking-host and CV-backend methods
- `Done` Update documentation indexes to include Wave 22

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `aethervr` as the main headsetless runtime comparison node instead of merging it into the camera-side driver family
- `Next` Revisit `MasonSakai/VR-AI-Full-Body-Tracking` only if its planned driver rewrite becomes more concrete
- `Next` Compare `Amethyst`, `Mediapipe-VR-Fullbody-Tracking`, and `HandOfLesser` directly as one `host platform vs backend switcher vs hand bridge` story
- `Next` Revisit `HandCameraDriver` only if the project revives or a cleaner maintained fork appears
