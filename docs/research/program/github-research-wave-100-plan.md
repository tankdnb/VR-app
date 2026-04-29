# GitHub Research Wave 100 Plan

- Date: `2026-04-30`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat avatar setup`, `optimization`, and `Quest portability`.

## Why this wave exists

`VR-apps-lab` already had much stronger coverage of VRChat creator worlds than
of `avatar authoring workbenches and build-time optimization paths`.

This wave exists to make the `avatar setup and shipping pipeline` branch
clearer.

## Search scope

Primary search directions for this wave:

- editor-side avatar workbenches and copier suites;
- Quest conversion helpers and mobile-target validation;
- upload-time avatar optimizers;
- avatar scaling and body-alignment preprocessors.

## Frozen shortlist for code-level study

- `rurre/PumkinsAvatarTools`
- `kurotu/VRCQuestTools`
- `d4rkc0d3r/d4rkAvatarOptimizer`
- `triazo/immersive_scaler`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `bigdayday/ShaderMotion`
  was more about avatar-side shader behavior than about the core setup or
  optimization pipeline;
- `Natsumi-sama/FACSvatar`
  looked more relevant as a future avatar-expression or viseme follow-up than
  as a setup or Quest-portability donor;
- `kurotu/VRCQuestAvatarShaders`
  overlapped strongly with the stronger conversion and optimization donors
  already frozen here.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for avatar setup, conversion, optimizer, and scaling queries;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where the setup, conversion, or optimization flow is visible in
  source.

### Step 2: Freeze the shortlist

- keep the wave centered on
  `avatar bring-up and shipping pipeline`
  rather than all avatar tools at once;
- allow both Unity-side and DCC-side donors when they clearly solve different
  parts of the pipeline.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how much of the value is editor shell versus deep pipeline logic;
- where configuration, validation, and asset replacement actually happen;
- which parts are narrow donors and which are broader product references.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 100 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- avatar tooling is treated as a first-class research branch rather than as
  accidental creator-side noise;
- broad tools are promoted only as far as the code-level pass supports;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 100 synthesis document exists with code-level findings;
4. the registry and families represent avatar setup and optimization donors
   more clearly;
5. new methods are captured where this wave clarified reusable setup,
   validation, conversion, or optimization patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
