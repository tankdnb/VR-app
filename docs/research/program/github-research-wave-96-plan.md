# GitHub Research Wave 96 Plan

- Date: `2026-04-27`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat creator starter baselines`, `test harnesses`, and
  `language-boundary experiments`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage of creator-world runtime systems
than of:

`the very first layer creators touch when they bootstrap a project, validate small Udon units, or try to smuggle non-Udon source languages into a creator-world pipeline`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- official or semi-official VRChat template repositories;
- creator-world testing helpers for Udon or UdonSharp;
- unusual code-generation or language-boundary experiments that target
  UdonSharp output;
- starter baselines that reveal package bootstrap or setup patterns.

## Frozen shortlist for code-level study

- `vrchat-community/template-world`
- `vrchat-community/template-udonsharp`
- `koyashiro/udon-test`
- `raii-x/wasm2usharp`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `vrchat-community/creator-docs`
  stayed outside this wave because the goal here is code-bearing bootstrap
  repos rather than documentation-only guidance;
- `vrchat-community/udonsharp-package-template`
  stayed outside this wave because the shortlist already had stronger baseline
  coverage through the official templates;
- several tiny creator templates surfaced, but they were weaker than the
  official template lineage and the `wasm2usharp` language-boundary donor.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for VRChat templates, Udon test helpers, and UdonSharp codegen
  experiments;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where the bootstrap or translation layer is visible in source.

### Step 2: Freeze the shortlist

- keep the wave centered on
  `bootstrap, test, and language-boundary substrate`
  rather than all creator tooling;
- allow one historical template variant when it clarifies a migration or
  lineage lesson.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how the bootstrap or setup flow works;
- whether the repo is a current baseline, a historical variant, or an
  experiment;
- what reusable patterns belong in the methods catalog.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 96 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- template lineage is described honestly;
- official starter baselines are kept distinct from deprecated variants;
- experimental codegen repos are described by their architecture, not just by
  novelty;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 96 synthesis document exists with code-level findings;
4. the registry and families represent creator bootstrap and test substrate
   more clearly;
5. new methods are captured where this wave clarified reusable setup, testing,
   or codegen patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
