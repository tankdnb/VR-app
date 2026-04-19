# GitHub Research Wave 27 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `motion compensation`,
  `calibration overlays`, and `spatial alignment tools`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenVR and OpenXR motion-compensation paths
- `Done` Search GitHub for tracker-space calibration overlays and continuous-calibration variants
- `Done` Search GitHub for eye-tracking calibration and alignment-adjacent room-capture tools
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Keep `PSVR2EyeTrackingCalibration` as a secondary calibration node because it is tied to a custom toolkit fork

## Work package B: Local source acquisition

- `Done` Confirm `OpenVR-MotionCompensation` in local cache
- `Done` Confirm `OpenXR-MotionCompensation` in local cache
- `Done` Confirm `OpenVR-SpaceCalibrator` in local cache
- `Done` Confirm `OpenVR-SpaceCalibrator2` in local cache
- `Done` Confirm `EyeTrackVR-OpenVR-Calibration-Overlay` in local cache
- `Done` Confirm `openvr-room-mapping` in local cache
- `Done` Confirm `PSVR2EyeTrackingCalibration` in local cache as a comparison node
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect driver hooks, shared library, and dashboard split in `OpenVR-MotionCompensation`
- `Done` Inspect API-layer and runtime-side compensation design in `OpenXR-MotionCompensation`
- `Done` Inspect core overlay plus driver-assisted calibration flow in `OpenVR-SpaceCalibrator`
- `Done` Inspect the continuous-calibration and metrics extensions in `OpenVR-SpaceCalibrator2`
- `Done` Inspect minimal overlay-first calibration flow in `EyeTrackVR-OpenVR-Calibration-Overlay`
- `Done` Inspect image-plus-pose capture pipeline in `openvr-room-mapping`

## Work package D: Repository updates

- `Done` Add Wave 27 plan document
- `Done` Add Wave 27 backlog document
- `Done` Add Wave 27 synthesis document
- `Done` Update the project registry for newly clarified calibration and alignment repos
- `Done` Update overlap families for motion compensation, calibration, and spatial alignment
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new alignment and spatial-capture methods
- `Done` Update documentation indexes to include Wave 27

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `PSVR2EyeTrackingCalibration` only as part of a future PSVR2-specific calibration or eye-tracking comparison wave
- `Next` Compare `OpenVR-MotionCompensation`, `OpenXR-MotionCompensation`, and `OpenVR-SpaceCalibrator2` directly as `driver hook`, `API layer`, and `continuous calibration` approaches
- `Next` Revisit `openvr-room-mapping` if a future wave needs stronger room-scan or environment-reconstruction overlap with passthrough research
