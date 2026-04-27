# GitHub Research Wave 99 Plan

- Date: `2026-04-27`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat world control gadgets`, `environmental systems`, and
  `specialized operator surfaces`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage of creator diagnostics, runtime
substrate, and embodied mechanics than of:

`small and medium world-control systems that do not fit neatly into one bucket: render-pipeline fixups, environmental controllers, operator lighting panels, and access-control surfaces`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- creator-world rendering or depth fixup helpers;
- stage-lighting or operator-control packages;
- synchronized environment controllers;
- keypad and world access-control prefabs.

## Frozen shortlist for code-level study

- `Varneon/VUdon-DepthBufferToolkit`
- `AcChosen/VR-Stage-Lighting`
- `tommaier123/UdonSharpDayNightController`
- `MolotovCherry/VRChat_Keypad`
- `KitKat4191/UdonKeypad`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `Sonic853/UdonLabToolkit`
  stayed outside this wave because the shortlist already had stronger concrete
  world-control surfaces instead of a broader mixed toolkit;
- several one-off world gadgets surfaced, but they were thinner than the
  lighting, environment, and keypad donors in the final scope.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for creator-world control surfaces, day-night systems, depth
  fixups, lighting panels, and keypad prefabs;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where the operator surface and the runtime control model are
  visible in source.

### Step 2: Freeze the shortlist

- keep the wave centered on
  `world-control gadgets and operator surfaces`
  rather than all creator prefabs;
- allow both tiny and broad repos when they represent clearly different control
  scales.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the repo is mostly editor tooling, runtime control, or both;
- how the control surface is exposed to creators or world operators;
- which parts are compact donors and which are broader references needing later
  follow-up.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 99 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- small control gadgets are treated as first-class donors when warranted;
- broader packages are promoted only as far as the code-level pass supports;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 99 synthesis document exists with code-level findings;
4. the registry and families represent creator-world operator surfaces more
   clearly;
5. new methods are captured where this wave clarified reusable control-surface,
   environment, or render-fixup patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
