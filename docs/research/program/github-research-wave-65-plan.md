# GitHub Research Wave 65 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `OpenXR language bindings`, `generator-backed wrappers`, and `SDK facades`.

## Why this wave exists

`VR-apps-lab` already had strong coverage of runtime tools and overlays, but it
still lacked a clearer family for
`how OpenXR gets wrapped, generated, or exposed to different host languages`.

This wave exists to make several donor branches explicit:

- `safe + raw` binding stacks;
- registry-driven code generation from `xr.xml`;
- build-integrated binding emitters;
- higher-level language facades that stay close to the native API.

## Search scope

Primary search directions for this wave:

- OpenXR bindings for Rust, Python, `.NET`, Zig, or adjacent systems languages;
- wrapper repos that generate code from the Khronos registry;
- higher-level facades that still expose loader resolution and dispatch logic
  clearly.

## Frozen shortlist for code-level study

- `Ralith/openxrs`
- `cmbruns/pyopenxr`
- `EvergineTeam/OpenXR.NET`
- `s-ol/openxr-zig`

## Secondary candidates surfaced in the same wave

- `drypy/openxr.py`
- `FireFlyForLife/rlOpenXR`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for OpenXR bindings, registry generators, and language-specific
  facades;
- compare results against `catalog/project-registry.md`;
- reject repos that are mostly engine demos without a distinct binding or
  wrapper lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `binding and wrapper construction`;
- allow lower-level repos when they expose generator boundaries or dispatch
  strategy clearly.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the binding surface is raw, ergonomic, or layered;
- how loader resolution and proc-address dispatch are handled;
- whether code is handwritten, generated from `xr.xml`, or emitted through a
  build step;
- whether the repo is strongest as a direct donor, an architecture reference,
  or a comparison node.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 65 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies binding
  generation and multi-layer API-wrapper patterns.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `OpenXR bindings` stay distinct from sample-app and runtime-tool families;
- the family clearly separates `safe/raw split`, `generated facade`,
  `.NET binding emitter`, and `build-integrated Zig generator` answers;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 65 synthesis document exists with code-level findings;
4. the registry and families clearly represent OpenXR binding donor lines;
5. new binding-construction methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
