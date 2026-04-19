# GitHub Research Wave 64 Backlog

- Date: `2026-04-19`
- Scope: next GitHub discovery wave focused on
  `OpenXR sample apps`, `rendering baselines`, and `bring-up references`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for OpenXR sample apps, graphics bring-up baselines, and minimal tutorial repos
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist that spans a one-file D3D11 bootstrap, a structured Vulkan sample app, a `wgpu` migration path, an Android GLES sample suite, and a minimal SDL or OpenGL baseline

## Work package B: Local source acquisition

- `Done` Confirm `OpenXRSamples` in local cache
- `Done` Confirm `openxr-vulkan-example` in local cache
- `Done` Confirm `wgpu-openxr-example` in local cache
- `Done` Confirm `android_openxr_gles` in local cache
- `Done` Confirm `openxr-simple-example` in local cache
- `Done` Confirm `OpenXR-Samples` as a surfaced comparison node
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect the one-file `D3D11` bootstrap, extension filtering, swapchain setup, and action-space flow in `OpenXRSamples`
- `Done` Inspect the `Context`, `Headset`, `Controllers`, and `MirrorView` split in `openxr-vulkan-example`
- `Done` Inspect the staged desktop-to-XR flow and `OpenXR + Vulkan + wgpu` glue in `wgpu-openxr-example`
- `Done` Inspect the shared utility core reused across multiple Android sample apps in `android_openxr_gles`
- `Done` Inspect the minimal SDL/OpenGL bring-up path in `openxr-simple-example`
- `Done` Confirm that `OpenXR-Samples` is still more useful as a comparison node than as the mainline donor in this pass

## Work package D: Repository updates

- `Done` Add Wave 64 plan document
- `Done` Add Wave 64 backlog document
- `Done` Add Wave 64 synthesis document
- `Done` Update the project registry for OpenXR bring-up samples and rendering baselines
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` with honest follow-up nodes where needed
- `Done` Update the methods catalog with new OpenXR bootstrap and sample-architecture methods
- `Done` Update documentation indexes to include Wave 64

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `OpenXRSamples` visible whenever a future branch needs `minimum viable OpenXR bootstrap` notes
- `Next` Keep `openxr-vulkan-example` visible whenever a future branch needs a more structured sample-app donor than a one-file tutorial
- `Next` Revisit `wgpu-openxr-example` whenever `VR-apps-lab` needs a stronger `desktop first, XR second` bring-up story
- `Next` Revisit `android_openxr_gles` whenever a future branch needs shared-core sample-suite comparisons
