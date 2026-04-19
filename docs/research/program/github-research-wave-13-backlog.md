# GitHub Research Wave 13 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `vision-based tracking`,
  `camera-driven hand/body bridges`, and `headsetless camera runtimes` that
  were not yet tracked in `VR-apps-lab`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for untracked SteamVR hand-tracking drivers
- `Done` Search GitHub for untracked webcam and camera-based full-body tracking paths
- `Done` Search GitHub for untracked Kinect and modular body-tracking platforms
- `Done` Search GitHub for headsetless camera runtime implementations
- `Done` Deduplicate all results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Record secondary candidates for future follow-up

## Work package B: Local source acquisition

- `Done` Confirm `ultraleap/driver_ultraleap` in local cache
- `Done` Confirm `Nordskog/HandOfLesser` in local cache
- `Done` Confirm `NovaAshwolfDev/HandCameraDriver` in local cache
- `Done` Confirm `KinectToVR/KinectToVR` in local cache
- `Done` Confirm `KinectToVR/Amethyst` in local cache
- `Done` Confirm `ju1ce/Mediapipe-VR-Fullbody-Tracking` in local cache
- `Done` Confirm `Wunder-Wulfe/NVIDIA-BodyTracking` in local cache
- `Done` Confirm `chnoblouch/aethervr` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect service-backed SteamVR hand-driver layering in `driver_ultraleap`
- `Done` Inspect OpenXR-to-SteamVR hand bridge and packet transport model in `HandOfLesser`
- `Done` Inspect Python-sidecar plus custom-driver WIP split in `HandCameraDriver`
- `Done` Inspect legacy multi-process Kinect/PSMove full-body stack in `KinectToVR`
- `Done` Inspect plugin and service-endpoint architecture in `Amethyst`
- `Done` Inspect single-camera body-tracking backends and WebUI flow in `Mediapipe-VR-Fullbody-Tracking`
- `Done` Inspect GPU-assisted body-tracking driver plus overlay split in `NVIDIA-BodyTracking`
- `Done` Inspect runtime-plus-tracker TCP split in `aethervr`

## Work package D: Repository updates

- `Done` Add Wave 13 plan document
- `Done` Add Wave 13 backlog document
- `Done` Add Wave 13 synthesis document
- `Done` Update project registry with newly studied repositories
- `Done` Update overlap families with the new nodes
- `Done` Update `not-yet-studied-deeply.md` with the new follow-up gaps
- `Done` Update methods catalog with Wave 13 tracking and runtime patterns
- `Done` Update documentation navigation to include Wave 13

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the main documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Deepen `Nordskog/HandOfLesser`, especially driver/app synchronization, controller-hooking mode, and VRChat-specific output boundaries
- `Next` Compare `KinectToVR/KinectToVR` and `KinectToVR/Amethyst` as one `legacy app to plugin-platform` migration story
- `Next` Deepen `Wunder-Wulfe/NVIDIA-BodyTracking`, especially overlay-assisted alignment, confidence handling, and tracker-role scaling
- `Next` Compare `ju1ce/Mediapipe-VR-Fullbody-Tracking`, `Wunder-Wulfe/NVIDIA-BodyTracking`, and `chnoblouch/aethervr` as one `camera-driven tracking backend` family
- `Next` Revisit `NovaAshwolfDev/HandCameraDriver` only if the project revives or a cleaner fork appears
- `Next` Inspect `ju1ce/Simple-OpenVR-Bridge-Driver` as a comparison node for generic tracker-ingress transport
- `Next` Inspect `MasonSakai/VR-AI-Full-Body-Tracking` if its planned driver rewrite becomes concrete
