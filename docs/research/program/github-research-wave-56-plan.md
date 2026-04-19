# GitHub Research Wave 56 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `browser-backed overlay runtimes`, `web-tech hosts`, and
  `UI runtime experiments`.

## Why this wave exists

`VR-apps-lab` already had overlay products, scene-native overlay extensions,
and thin `UI-to-texture` bridges, but another adjacent branch still needed a
cleaner donor map:

- native overlay backends that launch or host browser-facing app runtimes;
- offscreen desktop UI runtimes whose rendered frames become overlay textures;
- overlay hosts that treat local `HTTP` or `IPC` contracts as the application
  boundary instead of baking every tool into one process;
- newer UI runtime experiments that show how far the overlay pattern can
  stretch beyond `Win32` or `ImGui`.

This wave exists to make
`browser-backed overlay runtimes, web-tech hosts, and UI runtime experiments`
clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- `Electron`, `CEF`, browser, and webview-based SteamVR overlay hosts;
- multi-process overlay platforms with local daemon or `HTTP` app contracts;
- experimental UI runtimes that render into `OpenVR` overlays;
- thin host repos where the main lesson is `app runtime boundary`, not a single
  finished end-user utility.

## Frozen shortlist for code-level study

- `mekanoe/ovrsalt`
- `mekanoe/electron-openvr`
- `joshperry/ovrly`
- `ephemeral-laboratories/ComposeVR`

## Secondary candidates surfaced in the same wave

- no additional secondary candidates were strong enough to displace the frozen
  shortlist

## Execution model

### Step 1: Search and deduplicate

- search GitHub for browser-backed overlay hosts, web-tech overlay runtimes,
  and `OpenVR` UI runtime experiments;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate already-studied overlay products without
  adding a clearer `host/runtime/app boundary` lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `runtime architecture`, not generic creator or
  media overlays;
- allow both polished hosts and experimental bridges when they expose a
  distinct overlay-runtime contract.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how the overlay backend and the browser or UI runtime are split;
- how textures are produced and handed to `OpenVR`;
- whether the app model is local `HTTP`, `IPC`, shared buffers, or direct frame
  capture;
- what parts are useful as code donors versus product references only.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 56 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies
  browser-backed overlay host and `UI runtime -> overlay texture` methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `browser-backed overlay runtimes` stay distinct from generic display-shell
  overlays;
- the family clearly separates `native backend plus web runtime`,
  `offscreen browser window mirroring`, and `experimental UI-runtime bridges`;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 56 synthesis document exists with code-level findings;
4. the registry and families clearly represent browser-backed overlay host
   patterns;
5. new runtime-host or `UI-to-overlay` methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
