# GitHub Research Wave 101 Plan

- Date: `2026-04-30`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat avatar composition`, `packaging`, and `install automation`.

## Why this wave exists

`VR-apps-lab` needed a clearer picture of the branch that sits between
`authoring avatar parts`
and
`shipping a reusable avatar package to a project`.

This wave exists to make the `composition and project-package pipeline`
clearer.

## Search scope

Primary search directions for this wave:

- non-destructive avatar composition systems;
- code-first composition facades over creator components;
- package and project managers for VRChat creator workflows;
- avatar-manager shells that copy, merge, and emit safe asset outputs.

## Frozen shortlist for code-level study

- `bdunderscore/modular-avatar`
- `hai-vr/modular-avatar-as-code`
- `vrc-get/vrc-get`
- `VRLabs/Avatars-3.0-Manager`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `VRChatUnityThings/VRChatUnityThings`
  was broader and thinner than the final shortlist and did not anchor one
  clear composition or packaging pattern;
- `nadena.dev/ndmf`
  mattered as background substrate, but this wave focused on
  higher-level consumer repos that expose stronger creator-facing product
  surfaces over that substrate.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for avatar composition, package manager, and install-automation
  queries;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where composition, packaging, or install decisions are visible
  in source.

### Step 2: Freeze the shortlist

- keep the wave centered on
  `avatar composition and project integration`
  rather than all avatar runtime features;
- allow one project manager entry because package movement is part of the same
  real workflow.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where composition logic ends and project-install or package management begins;
- how much of the value is GUI versus reusable helper APIs;
- which repos are narrow component shells and which are broader workflow
  platforms.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 101 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- avatar composition is represented as a real reusable branch instead of
  disappearing into generic creator tooling;
- package-manager and install-flow lessons are captured explicitly;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 101 synthesis document exists with code-level findings;
4. the registry and families represent composition and packaging donors more
   clearly;
5. new methods are captured where this wave clarified composition, package, or
   install-automation patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
