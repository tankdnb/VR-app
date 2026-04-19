# GitHub Research Wave 12 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on synthetic devices,
  input-emulation sidecars, DIY/custom-hardware drivers, and
  motion-manipulation paths that were not yet tracked in `VR-apps-lab`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for untracked synthetic-controller and controller-emulation drivers
- `Done` Search GitHub for untracked legacy peripheral bridge drivers
- `Done` Search GitHub for untracked DIY HMD/controller OpenVR paths
- `Done` Search GitHub for InputEmulator-based sidecars and hybrid device helpers
- `Done` Search GitHub for motion-compensation and pose-rewrite driver paths
- `Done` Deduplicate all results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Record a secondary candidate for future follow-up

## Work package B: Local source acquisition

- `Done` Confirm `ValveSoftware/driver_hydra` in local cache
- `Done` Confirm `alatnet/OpenPSVR` in local cache
- `Done` Confirm `r57zone/OpenVR-driver-for-DIY` in local cache
- `Done` Confirm `gpsnmeajp/SegsVRControllerDriverSample` in local cache
- `Done` Confirm `puresoul/Barebone` in local cache
- `Done` Confirm `mmorselli/Joy2OpenVR` in local cache
- `Done` Confirm `mdovgialo/SteamVR-Glove` in local cache
- `Done` Confirm `openvrmc/OpenVR-MotionCompensation` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect official peripheral-bridge and calibration-monitor patterns in `driver_hydra`
- `Done` Inspect unified HMD/display driver layering in `OpenPSVR`
- `Done` Inspect sample-derived DIY HMD/controller path in `OpenVR-driver-for-DIY`
- `Done` Inspect shared-memory driver-plus-client pattern in `SegsVRControllerDriverSample`
- `Done` Inspect XInput-driven synthetic Vive controller pattern in `Barebone`
- `Done` Inspect DirectInput-to-InputEmulator sidecar mapping in `Joy2OpenVR`
- `Done` Inspect Arduino-plus-InputEmulator glove proof of concept in `SteamVR-Glove`
- `Done` Inspect pose-rewrite driver plus dashboard split in `OpenVR-MotionCompensation`

## Work package D: Repository updates

- `Done` Add Wave 12 plan document
- `Done` Add Wave 12 backlog document
- `Done` Add Wave 12 synthesis document
- `Done` Update project registry with newly studied repositories
- `Done` Update overlap families with the new nodes
- `Done` Update `not-yet-studied-deeply.md` with the new follow-up gaps
- `Done` Update methods catalog with Wave 12 device-side patterns
- `Done` Update documentation navigation to include Wave 12

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the main documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Deepen `alatnet/OpenPSVR`, especially controller, camera, and installer boundaries
- `Next` Deepen `openvrmc/OpenVR-MotionCompensation` around hook boundaries and overlay/library coordination
- `Next` Compare `puresoul/Barebone`, `mmorselli/Joy2OpenVR`, `mdovgialo/SteamVR-Glove`, and `matzman666/OpenVR-InputEmulator` as one `synthetic device and input-emulation sidecar` family
- `Next` Compare `ValveSoftware/driver_hydra`, `alatnet/OpenPSVR`, `r57zone/OpenVR-driver-for-DIY`, `r57zone/OpenVR-ArduinoHMD`, and `verncat/RayNeo-Air-3S-Pro-OpenVR` as one `legacy and niche hardware bridge` family
- `Next` Deep pass `verncat/RayNeo-Air-3S-Pro-OpenVR` if the repository grows from SDK scaffolding into a clearer driver or bridge path
