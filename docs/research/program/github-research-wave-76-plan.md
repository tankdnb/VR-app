# GitHub Research Wave 76 Plan

- Date: `2026-04-20`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `OpenXR capability-injection layers`, `input remappers`, and
  `peripheral extension bridges`.

## Why this wave exists

`VR-apps-lab` already had good coverage of OpenXR diagnostics, runtime
inspectors, and view-shaping micro-layers, but it still lacked a cleaner map of
the OpenXR layers that:

- add capabilities a runtime does not ship natively;
- override or reshape runtime-provided extension behavior;
- bridge external input or peripheral state into OpenXR semantics;
- act as the smallest reusable baseline for new capability-injection layers.

This wave exists to make those donor lines explicit.

## Search scope

Primary search directions for this wave:

- OpenXR API layers that add or override hand tracking or haptics;
- OpenXR remapping or action-layer repos;
- minimal Rust or C++ API-layer baselines;
- layer repos that bridge external runtimes or peripherals into OpenXR.

## Frozen shortlist for code-level study

- `ultraleap/OpenXRHandTracking`
- `Sorenon/openxr_remapping_layer`
- `verncat/OpenXR_ApiLayer_Patstrap`

## Secondary candidates surfaced in the same wave

These candidates overlapped with already-tracked layer families strongly enough
that they did not justify widening this wave:

- `Rectus/openxr-steamvr-passthrough`
- `LordOfDragons/openxr_oscclient`
- `DesktopXR`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for hand-tracking, remapping, and capability-injection layers;
- compare results against `catalog/project-registry.md`;
- prefer repos that expose new OpenXR layer roles rather than repeating already
  covered runtime inspectors or view-shaping layers.

### Step 2: Freeze the shortlist

- keep the wave centered on `capability injection and remapping`, not generic
  layer templates only;
- allow both mature repos and lower-bound skeletons when they teach different
  integration boundaries.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how loader negotiation and `xrGetInstanceProcAddr` interception are handled;
- whether the layer injects new capabilities, overrides existing ones, or
  remaps input semantics;
- where runtime detection, wrapper state, and external runtime ownership live;
- whether the repo is strongest as a code donor, a product reference, or a
  lower-bound bootstrap.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 76 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- capability-injection layers stay distinct from view-shaping or diagnostics
  layers;
- thin public snapshots are described honestly;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 76 synthesis document exists with code-level findings;
4. the registry and families represent these OpenXR capability-layer donors
   more clearly;
5. new methods are captured where this wave clarified reusable patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
