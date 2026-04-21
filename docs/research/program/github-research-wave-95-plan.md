# GitHub Research Wave 95 Plan

- Date: `2026-04-21`
- Goal: run the next focused GitHub research wave for repositories that map
  `Udon data-structure libraries`, `serialization helpers`, and
  `creator utility foundations`.

## Why this wave exists

`VR-apps-lab` already had better coverage of creator-world prefabs than of
`the lower-level libraries and utility substrate that make larger creator systems easier to build`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- Udon or UdonSharp collection libraries;
- JSON or serialization helpers for creator worlds;
- array-extension layers used when native data containers are insufficient;
- broad creator utility foundations with lifecycle, singleton, or helper
  infrastructure.

## Frozen shortlist for code-level study

- `Guribo/UdonUtils`
- `koyashiro/udon-list`
- `koyashiro/udon-dictionary`
- `koyashiro/udon-json`
- `hoke946/UArrayCollections`
- `Varneon/VUdon-ArrayExtensions`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `koyashiro/udon-encoding`, `udon-jwt`, and `udon-sha2`
  stayed outside this wave because the main value here is general creator data
  substrate rather than narrow protocol or cryptography helpers;
- `xiphia/UdonSharpCryptography`
  stayed outside this wave because it fits better in a future security or
  protocol micro-utility pass;
- `aiczk/ULinq`
  stayed outside this pass because the shortlist already had stronger array and
  collection baselines.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for Udon collection, JSON, and creator utility foundation
  repositories;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where data or lifecycle abstractions are clear in source.

### Step 2: Freeze the shortlist

- keep the wave centered on `creator-world utility substrate`, not on all
  creator packages;
- allow both broad utility foundations and narrow collection libraries when
  they clarify different abstraction layers.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- what the abstraction boundary is: lifecycle, singleton, execution order,
  list, dictionary, JSON, or array extension;
- whether the repo predates newer VRChat native containers and is therefore now
  a historical reference rather than a greenfield recommendation;
- what reusable lower-layer methods belong in the methods catalog.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 95 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- historical pre-native-container libraries are described honestly;
- broad utility foundations are kept distinct from small collection helpers;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 95 synthesis document exists with code-level findings;
4. the registry and families represent creator-world data substrate more
   clearly;
5. new methods are captured where this wave clarified reusable lower-layer
   patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
