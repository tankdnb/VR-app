# GitHub Research Wave 24 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `accessibility captions`,
  `assistive speech surfaces`, and `micro-HUD accessibility utilities`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for SteamVR/OpenVR caption overlays and local speech-recognition utilities
- `Done` Search GitHub for browser-first or desktop caption tools that can still feed VR surfaces
- `Done` Search GitHub for mic-state and push-to-talk overlays with an assistive angle
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Keep `eepyxr` and `TurnSignal` as family references instead of over-expanding the wave

## Work package B: Local source acquisition

- `Done` Confirm `Vinventive/live-captions-vr` in local cache
- `Done` Confirm `MochiDoesVR/OpenVRCaptions` in local cache
- `Done` Confirm `ctobin1114/UniversalVR-CC` in local cache
- `Done` Confirm `gt0777/VRCLiveCaptionsMod` in local cache
- `Done` Confirm `I5UCC/VRCTextboxSTT` in local cache
- `Done` Confirm `rrazgriz/VRCMicOverlay` in local cache
- `Done` Confirm `matzman666/OpenVR-MicrophoneControl` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect Python speech sidecar plus Unity/OpenVR overlay split in `live-captions-vr`
- `Done` Inspect WPF settings shell and Direct2D/OpenVR renderer in `OpenVRCaptions`
- `Done` Inspect Flask or SocketIO browser-caption service flow in `UniversalVR-CC`
- `Done` Inspect game-internal audio-hook and subtitle worker design in `VRCLiveCaptionsMod`
- `Done` Inspect multi-output transcription plus SteamVR overlay path in `VRCTextboxSTT`
- `Done` Inspect mic-state sensing and minimal overlay loop in `VRCMicOverlay`
- `Done` Inspect dashboard-side audio-control overlay flow in `OpenVR-MicrophoneControl`

## Work package D: Repository updates

- `Done` Add Wave 24 plan document
- `Done` Add Wave 24 backlog document
- `Done` Add Wave 24 synthesis document
- `Done` Update the project registry for newly clarified accessibility repos
- `Done` Update overlap families for captions, assistive HUDs, and mic-state tools
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new accessibility-overlay methods
- `Done` Update documentation indexes to include Wave 24

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Compare `live-captions-vr`, `OpenVRCaptions`, and `VRCTextboxSTT` directly as `native overlay renderer` versus `multi-output transcription host`
- `Next` Revisit `UniversalVR-CC` only if a future wave needs more `browser-first utility host` references
- `Next` Revisit `VRCLiveCaptionsMod` only when a later research pass wants app-internal speech-hook examples rather than generic overlay utilities
