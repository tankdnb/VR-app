# GitHub Research Wave 20 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `performance mods`,
  `runtime-aware graphics injection`, and `VR sweet-spot shader bundles`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for extended `vrperfkit` forks and D3D proxy variants
- `Done` Search GitHub for public VR foveation experiments with a visible code path
- `Done` Search GitHub for VR-focused shader bundles and generic injection donors
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Record `shieldmeidunn/SteamVRNullFlipper` as a follow-up signal instead of over-expanding the wave

## Work package B: Local source acquisition

- `Done` Confirm `RavenSystem/VRPerfKit_RSF` in local cache
- `Done` Confirm `CamelCaseName/OpenVRPerfKit` in local cache
- `Done` Confirm `Granther/foveated-rendering` in local cache
- `Done` Confirm `retroluxfilm/reshade-vrtoolkit` in local cache
- `Done` Confirm `zhukovv/upscale-injection` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect extended config surface, dynamic modes, and DLL chaining in `VRPerfKit_RSF`
- `Done` Inspect backend expansion and FSR2 packaging in `OpenVRPerfKit`
- `Done` Inspect focus-source assumptions and actual implementation state in `foveated-rendering`
- `Done` Inspect the shader bundle and combined image-treatment surface in `reshade-vrtoolkit`
- `Done` Inspect the generic D3D11 hook plumbing in `upscale-injection`

## Work package D: Repository updates

- `Done` Add Wave 20 plan document
- `Done` Add Wave 20 backlog document
- `Done` Add Wave 20 synthesis document
- `Done` Update the project registry for the newly clarified rendering-mod repos
- `Done` Update overlap families for performance and rendering tooling
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new rendering-mod methods
- `Done` Update documentation indexes to include Wave 20

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `Granther/foveated-rendering` only if the public repo grows a real eye-tracker ingestion path beyond the current cursor-driven experiment
- `Next` Compare `VRPerfKit_RSF` and `OpenVRPerfKit` directly as one `fork lineage vs backend expansion` story
- `Next` Inspect `shieldmeidunn/SteamVRNullFlipper` if the null-driver and focus-window trick becomes useful for headsetless graphics testing
- `Next` Decide whether `reshade-vrtoolkit` deserves a small dedicated reuse plan as a `single-pass VR shader bundle` donor
