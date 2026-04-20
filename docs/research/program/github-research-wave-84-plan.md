# GitHub Research Wave 84 Plan

- Date: `2026-04-20`
- Goal: run the next focused GitHub research wave for repositories that map
  `browser panoramic video players`, `mobile wrappers`, and
  `projection-aware web playback plugins`.

## Why this wave exists

`VR-apps-lab` already had broader immersive playback coverage, but it still
lacked a cleaner answer to:

`what the strongest projection-aware playback donors look like when the player is web-first, plugin-shaped, or wrapped as a thin mobile bridge`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- browser 360 or VR video players;
- Video.js or HTML5-player plugins with explicit projection support;
- mobile wrappers that expose 360 playback through thin XR or native bridges;
- panoramic-player repos where stereoscopy or projection is modeled explicitly.

## Frozen shortlist for code-level study

- `BIVROST/360WebPlayer`
- `yanwsh/videojs-panorama`
- `videojs/videojs-vr`
- `flutterwtf/VR-Player`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `mpetroff/pannellum`
  useful panorama-viewer context, but not a strong enough `video-player`
  donor for this wave;
- already tracked playback nodes such as `360PlayerWindows` and
  `WebXR-video-player`
  remained comparison anchors instead of widening the wave.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for panoramic web video players, projection-aware plugins, and
  mobile VR video wrappers;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos that expose projection, stereoscopy, or renderer boundaries
  clearly in source.

### Step 2: Freeze the shortlist

- keep the wave centered on `projection-aware playback architecture`, not just
  general panorama viewers;
- allow both framework-like plugins and thin product wrappers when they reveal
  different boundaries cleanly.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how media sources, projection modes, and stereoscopy are represented;
- where renderer or canvas backends split from ordinary playback controls;
- whether the repo is strongest as a donor, plugin baseline, or product
  wrapper reference;
- how much of the public UX depends on filename heuristics, config, or
  explicit user selection.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 84 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- web playback plugins stay distinct from broader immersive media shells;
- thin mobile wrappers are described honestly when their strongest value is
  bridge shape rather than deep media architecture;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 84 synthesis document exists with code-level findings;
4. the registry and families represent browser and mobile panoramic playback
   donors more clearly;
5. new methods are captured where this wave clarified reusable web or wrapper
   patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
