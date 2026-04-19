# GitHub Research Wave 66 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `OpenVR language bindings`, `managed wrappers`, and `scripting access layers`.

## Why this wave exists

`VR-apps-lab` already had many OpenVR overlays and drivers, but it still lacked
clearer donor coverage for
`how OpenVR itself gets wrapped and exposed to different host languages`.

This wave exists to make several binding-oriented branches explicit:

- typed wrappers with explicit subsystem handles;
- scripting-first access layers;
- native-addon or `cgo` bridges into higher-level runtimes;
- object-oriented `.NET` facades over the OpenVR SDK.

## Search scope

Primary search directions for this wave:

- OpenVR bindings for Rust, Python, Go, Node.js, `.NET`, or adjacent
  host-language surfaces;
- repos that expose interface loading, typed enums, or runtime lifecycle
  boundaries clearly;
- wrapper projects that include enough example usage to act as donors.

## Frozen shortlist for code-level study

- `rust-openvr/rust-openvr`
- `cmbruns/pyopenvr`
- `tbogdala/openvr-go`
- `node-xr/node-openvr`
- `Flutterish/OpenVR.NET`

## Secondary candidates surfaced in the same wave

- `java-graphics/openvr`
- `matinas/openvrsimplexamples`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for OpenVR bindings, managed wrappers, and scripting access
  layers;
- compare results against `catalog/project-registry.md`;
- reject repos that are mostly app-specific overlays without a distinct wrapper
  lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `language-level OpenVR access`;
- allow wrapper repos when they expose lifecycle and interface boundaries
  clearly even if they are not polished end-user products.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how initialization and shutdown are represented;
- whether subsystem interfaces are wrapped as typed handles or raw calls;
- how the binding crosses from native code into the host language;
- whether the repo is strongest as a direct donor, a wrapper-pattern reference,
  or a comparison node.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 66 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies OpenVR
  wrapper and runtime-facade patterns.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `OpenVR bindings` stay distinct from overlay, driver, and tracker-export
  families;
- the family clearly separates `typed wrapper`, `ctypes scripting surface`,
  `cgo bridge`, `native addon`, and `.NET facade` answers;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 66 synthesis document exists with code-level findings;
4. the registry and families clearly represent OpenVR binding donor lines;
5. new OpenVR wrapper methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
