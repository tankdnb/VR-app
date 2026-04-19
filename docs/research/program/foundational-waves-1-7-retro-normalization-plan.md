# Foundational Waves 1-7 Retro Normalization Plan

- Date: `2026-04-19`
- Goal: bring the pre-Wave-8 research corpus up to the same standard used by
  Waves `8-13`, with an explicit audit, a frozen re-study shortlist, and
  canonical updates to the registry, families, methods, and backlog.

## Why this pass exists

The early `VR-apps-lab` research corpus is valuable, but it was created before
the repository settled on the current `plan -> backlog -> shortlist -> local
source sync -> code-level pass -> canonical integration` workflow.

That created four problems:

- `waves 1-2` effectively lived inside `vr-utilities-repo-landscape.md`
  instead of separate wave documents;
- Waves `3-7` mixed broad discovery, gap-fill notes, and deeper passes without
  one shared structure;
- several repositories were promoted into the registry with light notes that no
  longer match the depth of Waves `8-13`;
- some early repos now need `status correction`, not only prettier wording.

## Scope

This normalization pass covers the foundational research sources:

- `docs/research/landscape/vr-utilities-repo-landscape.md`
- `docs/research/landscape/vr-projects-wave-3-utilities.md`
- `docs/research/landscape/vr-projects-wave-4-gap-fill.md`
- `docs/research/landscape/vr-projects-wave-5-osc-tracking-tools.md`
- `docs/research/landscape/vr-projects-wave-6-driver-bridges.md`
- `docs/research/landscape/vr-projects-wave-7-depth-pass.md`

## Audit goals

1. recover which families and repositories entered the repo through the
   foundational waves;
2. compare those repositories against the current `project-registry`,
   `project-families`, and `not-yet-studied-deeply` state;
3. identify which entries were already strong enough and which ones still
   needed a true code-level re-pass;
4. create one canonical retro-normalization landscape document that complements
   the historical early-wave docs instead of replacing them.

## Frozen shortlist for repeat deep-pass

These repositories were selected because they were still strategically
important for `VR-apps-lab`, but were either under-detailed or still marked too
loosely compared with the newer wave standard.

- `BnuuySolutions/PSVR2Toolkit`
- `MuffinTastic/steamvr-exconfig`
- `zeroae/VRBattery`
- `John-Dean/OpenVR-Tracker-Websocket-Driver`
- `surplex-io/OpenVR-Driver`
- `gpsnmeajp/VirtualMotionTracker`
- `RedHawk989/EyeTrackVR-OpenVR-Calibration-Overlay`
- `WiiPlayer2/VnotifieR`
- `BenWoodford/OVROverlayManager`
- `mittorn/ovr-utils-dashboard`

## Execution model

### Step 1: Audit the early corpus

- treat `vr-utilities-repo-landscape.md` as the functional equivalent of the
  missing `waves 1-2`;
- map the early corpus against the modern registry and family structure;
- distinguish between `historically useful` notes and `still under-normalized`
  repositories.

### Step 2: Freeze a bounded normalization shortlist

- avoid re-reviewing every early repo blindly;
- focus on under-normalized nodes that still matter as:
  - `code donor`
  - `product reference`
  - `architecture reference`

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep every source clone local-only and outside git tracking.

### Step 4: Perform the repeat code-level pass

For each shortlisted repo inspect:

- current repository state and recent commit shape;
- README and actual product framing;
- module boundaries, entry points, and helper-process splits;
- overlay/runtime/input/config/IPC structure;
- what is still worth copying conceptually and what is not.

### Step 5: Promote findings into canonical docs

Update:

- one new foundational retro-normalization landscape document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` if a new reusable method becomes
  explicit;
- documentation indexes that should now point at the retro-normalization pass.

### Step 6: Verify before publishing

For this class of work, the main checks are:

- old-wave context is still preserved instead of erased;
- the retro-normalization document is linked from the research indexes;
- status changes are reflected consistently in the registry and families;
- `.research-sources/` stays ignored by git;
- the new pass clarifies follow-up gaps instead of hiding them.

## Definition of done

This normalization pass is complete when:

1. the early corpus has an explicit audit summary;
2. a frozen shortlist of under-normalized foundational repos is restudied from
   local source;
3. a canonical `foundational waves 1-7 retro-normalization` landscape document
   exists;
4. registry, families, backlog, and methods reflect the restudy;
5. documentation indexes point at the new canonical pass;
6. the result is reviewed and ready to publish.
