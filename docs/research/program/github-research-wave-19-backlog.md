# GitHub Research Wave 19 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on `vendor enhancement tooling`,
  `repurposed output bridges`, and `alternative hardware paths`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for vendor-enhancement projects that wrap official headset stacks
- `Done` Search GitHub for AR-glasses and repurposed-display OpenVR paths
- `Done` Search GitHub for sparse but relevant virtual-hardware driver signals
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist for code-level inspection
- `Done` Record `OpenDisplayXR/OpenDisplayXR-VDD` as a source-light signal instead of over-promoting it

## Work package B: Local source acquisition

- `Done` Confirm `BnuuySolutions/PSVR2Toolkit` in local cache
- `Done` Confirm `krazysh01/VirtualDesktop-OpenVR-Trackers` in local cache
- `Done` Confirm `verncat/RayNeo-Air-3S-Pro-OpenVR` in local cache
- `Done` Confirm `alatnet/OpenPSVR` in local cache
- `Done` Confirm `OpenDisplayXR/OpenDisplayXR-VDD` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect driver wrapping, IPC, and hook surfaces in `PSVR2Toolkit`
- `Done` Inspect the public `VirtualDesktop-OpenVR-Trackers` snapshot far enough to classify its current donor quality honestly
- `Done` Inspect the SDK and stub-driver split in `RayNeo-Air-3S-Pro-OpenVR`
- `Done` Inspect the HMD driver, display setup, and sensor path in `OpenPSVR`
- `Done` Inspect `OpenDisplayXR-VDD` far enough to keep it labeled as source-light

## Work package D: Repository updates

- `Done` Add Wave 19 plan document
- `Done` Add Wave 19 backlog document
- `Done` Add Wave 19 synthesis document
- `Done` Update the project registry for the newly clarified vendor and hardware repos
- `Done` Update overlap families for vendor enhancement and repurposed-display paths
- `Done` Update `not-yet-studied-deeply.md` with the remaining honest follow-ups
- `Done` Update the methods catalog with new vendor-wrapper and output-bridge methods
- `Done` Update documentation indexes to include Wave 19

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Done` Commit the wave results
- `Done` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `PSVR2Toolkit` with a tighter scope around eye tracking, calibration limits, and the public developer API surface
- `Next` Revisit `RayNeo-Air-3S-Pro-OpenVR` only after the dedicated driver repo matures beyond the current stub baseline
- `Next` Revisit `VirtualDesktop-OpenVR-Trackers` only if the public repo evolves beyond its currently thin tutorial-derived snapshot
- `Next` Revisit `OpenDisplayXR-VDD` only when more than a one-line project signal is publicly available
