# GitHub Research Wave 85 Plan

- Date: `2026-04-20`
- Goal: run the next focused GitHub research wave for repositories that map
  `engine-side stereo panoramic viewers`, `vendor player samples`, and
  `layout-specific video surfaces`.

## Why this wave exists

`VR-apps-lab` already had broad media-shell coverage, but it still lacked a
clearer answer to:

`what the best engine-side donors look like when immersive video playback is modeled as scene components, layout modes, or vendor reference scenes instead of a whole desktop shell`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- Unity panoramic or stereoscopic viewer components;
- Unreal or engine demo repos for stereo panoramic playback;
- vendor XR samples that demonstrate multiple video layout modes;
- repos where image and video playback share the same spherical or panoramic
  projection substrate.

## Frozen shortlist for code-level study

- `ft-lab/Unity_Panorama180View`
- `picoxr/VideoPlayer-UnityXR`
- `UNAmedia/ue5-stereo-panoramic-player-demo`

## Secondary candidates surfaced in the same wave

These nodes remained comparison context instead of widening the wave:

- `BIVROST/360PlayerWindows`
  already covered as a desktop media-shell reference;
- `videolan/vlc-unity`
  already covered as a broader engine media substrate instead of a narrower
  panoramic-viewer donor.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for Unity, Unreal, and vendor XR panoramic playback samples;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos that teach projection layout, component split, or reusable
  scene architecture.

### Step 2: Freeze the shortlist

- keep the wave centered on `engine-side playback surfaces`;
- allow both open-source components and demo clients when they still teach a
  strong product or architecture split.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how video layout modes are represented in code or scenes;
- where spherical projection, material selection, or shader paths live;
- whether the repo is strongest as a donor component, vendor reference, or
  product architecture note;
- how much of the UX sits in reusable scene components versus editor setup.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 85 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- vendor samples are described honestly when they are stronger as layout
  references than as reusable frameworks;
- demo-only repos are not overstated as full donors when the main plugin is
  external;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 85 synthesis document exists with code-level findings;
4. the registry and families represent engine-side panoramic playback donors
   more clearly;
5. new methods are captured where this wave clarified component, shader, or
   vendor-scene patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
