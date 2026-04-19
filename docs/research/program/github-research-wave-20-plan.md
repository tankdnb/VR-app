# GitHub Research Wave 20 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `performance mods`, `runtime-aware graphics injection`, and
  `VR sweet-spot shader bundles`.

## Why this wave exists

After Wave 19 the repository had much stronger coverage of:

- overlays, tracker bridges, and runtime-side utility shells;
- driver tutorials, hardware bridges, and vendor-wrapper tooling;
- OpenXR runtime managers, API layers, and diagnostics tools.

What still needed a clearer pass was the family where:

- a utility does not live at the overlay or driver level, but inside the
  graphics path itself;
- `DXGI proxy DLLs`, `d3d11.dll` hooks, and post-process chains are the real
  product boundary;
- public repositories range from polished donor-grade forks to promising but
  still incomplete experiments.

This wave exists to keep `performance and rendering utilities` represented as
their own coherent product family rather than as a side note under generic VR
graphics mods.

## Search scope

Primary search directions for this wave:

- `vrperfkit` forks and extended D3D11/DXGI proxy variants;
- OpenVR/OpenXR foveation experiments that expose new config or focus-source
  patterns;
- post-process shader bundles shaped for VR rather than generic flat-screen
  games;
- adjacent generic upscaling or injection repos when they teach reusable hook
  mechanics for VR tooling.

## Frozen shortlist for code-level study

- `RavenSystem/VRPerfKit_RSF`
- `CamelCaseName/OpenVRPerfKit`
- `Granther/foveated-rendering`
- `retroluxfilm/reshade-vrtoolkit`
- `zhukovv/upscale-injection`

## Secondary candidate surfaced in the same wave

- `shieldmeidunn/SteamVRNullFlipper`

## Execution model

### Step 1: Search and deduplicate

- search GitHub by `vrperfkit`, `foveated rendering`, `OpenVR post process`,
  and `DXGI proxy` family queries;
- compare candidates against `catalog/project-registry.md`;
- reject repos that are only trivial mirrors unless they extend the config
  model, backend coverage, or shader packaging in a meaningful way.

### Step 2: Freeze the shortlist

- keep the wave bounded around `graphics-path utilities`, not general engine
  mods;
- prefer repositories that expose a clear DLL boundary, shader bundle, or
  runtime-facing injection model.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- proxy DLL layout and original-DLL chaining strategy;
- config surface for scaling, foveation, masks, or sharpening;
- graphics backend coverage such as `D3D11`, `D3D12`, or OpenXR-specific paths;
- whether the repo is a practical donor, an experimental focus-source branch,
  or mainly a shader-packaging reference.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 20 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave sharpens reusable
  rendering-mod and shader-bundle methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- rendering-mod entries stay separated from runtime-layer and overlay families;
- donor quality remains labeled honestly, especially for experimental repos;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave and the family map stays coherent.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 20 synthesis document exists with code-level findings;
4. newly clarified repos are promoted or reclassified in the registry and
   families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
