# Foundational Waves 1-7 Retro Normalization Backlog

- Date: `2026-04-19`
- Scope: normalize the foundational `VR-apps-lab` research corpus from the
  equivalent of `waves 1-7` so it matches the quality bar and structure used by
  Waves `8-13`.

## Status legend

- `Done`
- `Next`

## Work package A: Foundational-wave audit

- `Done` Audit `vr-utilities-repo-landscape.md` as the functional equivalent of `waves 1-2`
- `Done` Audit Waves `3-7` against the current registry and family map
- `Done` Identify which early-wave repos were already mature enough and which remained under-normalized
- `Done` Freeze a bounded shortlist for repeat code-level study

## Work package B: Local source acquisition

- `Done` Confirm `BnuuySolutions/PSVR2Toolkit` in local cache
- `Done` Confirm `MuffinTastic/steamvr-exconfig` in local cache
- `Done` Confirm `zeroae/VRBattery` in local cache
- `Done` Confirm `John-Dean/OpenVR-Tracker-Websocket-Driver` in local cache
- `Done` Confirm `surplex-io/OpenVR-Driver` in local cache
- `Done` Confirm `gpsnmeajp/VirtualMotionTracker` in local cache
- `Done` Confirm `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay` in local cache
- `Done` Confirm `WiiPlayer2/VnotifieR` in local cache
- `Done` Confirm `BenWoodford/OVROverlayManager` in local cache
- `Done` Confirm `mittorn/ovr-utils-dashboard` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Repeat code-level deep pass

- `Done` Re-study `PSVR2Toolkit` around vendor-driver wrapping, hook boundaries, and versioned IPC
- `Done` Re-study `steamvr-exconfig` around SteamVR settings rewrite and backup-safe config patching
- `Done` Re-study `VRBattery` around micro-overlay structure and offscreen widget rendering
- `Done` Re-study `OpenVR-Tracker-Websocket-Driver` around driver-hosted WebSocket plus HTTP service architecture
- `Done` Compare `surplex-io/OpenVR-Driver` against the John-Dean upstream line
- `Done` Re-study `VirtualMotionTracker` around driver-manager split, OSC transport, and skeletal input
- `Done` Re-study `EyeTrackVR-OpenVR-Calibration-Overlay` around the overlay-first 9-point calibration flow
- `Done` Re-study `VnotifieR` around local HTTP notification ingress and panel fade behavior
- `Done` Re-study `OVROverlayManager` around Unity overlay toolkit scaffolding and input bridging
- `Done` Re-study `ovr-utils-dashboard` around Godot overlay-shell composition and settings-driven overlay instances

## Work package D: Repository updates

- `Done` Add foundational retro-normalization plan document
- `Done` Add foundational retro-normalization backlog document
- `Done` Add foundational retro-normalization landscape document
- `Done` Update project registry with corrected foundational-wave statuses
- `Done` Update overlap families with the re-studied nodes and corrected notes
- `Done` Update `not-yet-studied-deeply.md` with the remaining foundational follow-ups
- `Done` Update methods catalog with the overlay-toolkit scaffolding method
- `Done` Update research indexes and documentation navigation to include the retro-normalization pass

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new retro-normalization pass is linked from the research indexes
- `Next` Commit the foundational normalization results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this normalization pass

- `Next` Revisit `CrispyPin/ovr-utils` through its non-GitHub upstream, because the GitHub mirror is no longer the real implementation source
- `Next` Deepen `PSVR2Toolkit` around vendor update fragility, closed-source boundaries, and real consumer use of the developer API
- `Next` Compare `John-Dean/OpenVR-Tracker-Websocket-Driver`, `ju1ce/Simple-OpenVR-Bridge-Driver`, `3NekoSystem/OpenVR-Tracker-Websocket-Driver`, and `v0xie/OpenVR-Tracker-Websocket-Driver` as one `generic tracker ingress` line
- `Next` Deepen `LucidVR/opengloves-driver`, `HoboVR-Labs/hobo_vr`, `DaniXmir/GlassVr`, and `terminal29/Simple-OpenVR-Driver-Tutorial` as one `custom-device learning path` cluster
- `Next` Compare `mittorn/ovr-utils-dashboard`, `openvr_widgets`, `OVRLay`, and `OVROverlayManager` as one `overlay toolkit versus finished utility shell` family
