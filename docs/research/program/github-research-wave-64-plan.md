# GitHub Research Wave 64 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `OpenXR sample apps`, `rendering baselines`, and `bring-up references`.

## Why this wave exists

`VR-apps-lab` already had strong coverage of overlays, runtime utilities,
bridges, and sidecars, but it still lacked a clearer donor branch for
`how a new OpenXR app actually gets brought up from zero`.

This wave exists to make several lower-bound construction patterns explicit:

- single-file OpenXR bring-up references;
- structured sample apps that split graphics, headset, and input concerns;
- desktop-to-XR migration paths;
- Android or GLES sample suites that reuse one shared OpenXR core.

## Search scope

Primary search directions for this wave:

- small or mid-sized OpenXR sample apps that expose loader, session, and
  graphics bring-up clearly;
- rendering baselines that show how Vulkan, OpenGL, or `wgpu` integrate with
  OpenXR;
- sample suites that share one OpenXR utility core across multiple focused
  example apps.

## Frozen shortlist for code-level study

- `maluoi/OpenXRSamples`
- `janhsimon/openxr-vulkan-example`
- `philpax/wgpu-openxr-example`
- `terryky/android_openxr_gles`
- `KHeresy/openxr-simple-example`

## Secondary candidates surfaced in the same wave

- `jherico/OpenXR-Samples`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for OpenXR sample apps, graphics bring-up repos, and minimal
  tutorial baselines;
- compare results against `catalog/project-registry.md`;
- reject repos that are mostly engine wrappers or official SDK mirrors without
  a distinct sample-app construction lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `OpenXR bring-up references`, not broad runtime
  tooling;
- allow repos with narrow scope when they expose a clean implementation split.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how instance, system, and session bring-up are staged;
- where graphics requirements and swapchain setup live;
- how action sets, spaces, and controller wiring are structured;
- whether the repo is strongest as a minimal baseline, a reusable scaffold, or
  a comparison node.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 64 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies OpenXR
  bring-up and sample-app architecture patterns.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `OpenXR bring-up` stays distinct from runtime-tooling and overlay families;
- the family clearly separates `single-file bootstrap`,
  `structured sample app`, `desktop-to-XR migration`, and
  `shared sample core` answers;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 64 synthesis document exists with code-level findings;
4. the registry and families clearly represent OpenXR sample-app donor lines;
5. new OpenXR bring-up methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
