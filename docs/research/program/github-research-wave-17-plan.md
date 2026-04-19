# GitHub Research Wave 17 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `OpenXR runtime managers`, `experimental API layers`, and
  `runtime-side service hosts`.

## Why this wave exists

After Waves 9 through 15 the repository had better coverage of:

- runtime switchers and doctor tools;
- overlay hosts and overlay scaffolds;
- tracker bridges and direct-to-consumer exporters;
- headsetless runtimes and camera-driven experiments.

What still needed a deeper pass was the boundary between:

- `runtime managers` that mainly discover and switch active manifests;
- `API layers` that inject new behavior or sensor data;
- `overlay layers` that create remote or out-of-process presentation models;
- `runtime-side service platforms` that mix registration, UI, and runtime
  integration in one stack.

## Search scope

Primary search directions for this wave:

- Windows runtime-manager utilities;
- experimental `OpenXR API layer` repositories;
- runtime-side service and registration hosts;
- OpenXR overlay-layer experiments;
- repos that sit between a foreign service protocol and OpenXR.

## Frozen shortlist for code-level study

- `PlutoVR/OpenXR-OverlayLayer-1`
- `Ybalrid/OpenXR-Runtime-Manager`
- `pembem22/etvr-openxr-layer`
- `clear-xr/clearxr-server`

## Secondary candidate surfaced in the same wave

- `vrkit-platform/vrkit-platform`

## Execution model

### Step 1: Search and deduplicate

- search by `runtime boundary` and `layer behavior`, not just by OpenXR name
  matches;
- compare candidates against `catalog/project-registry.md`;
- reject duplicates unless they reveal a meaningfully different registration,
  probing, or API-layer pattern.

### Step 2: Freeze the shortlist

- keep the wave bounded around `runtime manager`, `overlay layer`, `protocol
  adapter layer`, and `runtime-side service host` roles;
- prefer repos that expose a clear architecture boundary instead of only a
  small settings tweak.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- README and actual product framing;
- whether the repo is a `runtime switcher`, `API layer`, `remote overlay
  client`, or `service host`;
- registration and manifest handling;
- whether privileged actions are separated into helpers;
- transport or IPC model for the layer or client;
- what makes it a donor versus only a product reference.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 17 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave sharpens remote
  overlay-layer, runtime-switching, and protocol-adapter layer methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- runtime/layer family placement remains coherent;
- large platforms such as `clearxr-server` stay labeled honestly if only one
  slice was studied deeply enough;
- scope-mismatched or domain-sprawled candidates remain follow-up items instead
  of being over-promoted;
- `.research-sources/` stays ignored by git.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 17 synthesis document exists with code-level findings;
4. newly studied repos are promoted or reclassified in the registry and
   families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
