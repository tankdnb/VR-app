# GitHub Research Wave 15 Plan

- Date: `2026-04-19`
- Goal: run the next serious GitHub research wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `overlay-first utility hosts`, `HUD micro-overlays`, `web or scene overlay
  scaffolds`, and `engine-side overlay integration` across `SteamVR/OpenVR`
  and adjacent `OpenXR` paths.

## Why this wave exists

After Wave 14, the repository had much stronger coverage of:

- tracker-ingress drivers and bridge transports;
- OSC export utilities and direct consumer bridges;
- no-HMD tracking adapters and camera-driven runtimes;
- runtime diagnostics, switching, and layer-management tools.

What was still thinner than it should be was the `overlay-construction` side of
the corpus:

- `overlay-first utility hosts` that are more about hosting useful UI surfaces
  than about one isolated utility;
- `HUD micro-overlays` that do one small comfort or monitoring job very well;
- `web-backed`, `WinForms/WPF-backed`, or `ImGui-backed` overlay shells that
  reuse an existing UI stack instead of inventing a custom VR-only UI system;
- `scene-overlay scaffolds` where Unity scene content, trackers, or sensors are
  composed into an overlay space;
- `engine-side OpenXR overlay entry points` that show where overlay support
  can be added inside a larger engine host.

## Search scope

Primary search directions for this wave:

- OpenVR dashboard overlays and overlay helper libraries;
- overlay projects built around `browser`, `WinForms`, `WPF`, `ImGui`, or
  `render-texture` reuse;
- wrist or watch overlays and HUD micro-utilities;
- scene-overlay and Unity overlay scaffold repos;
- engine-side OpenXR overlay integration samples;
- micro-overlays that patch an existing SteamVR surface instead of building a
  whole utility shell.

## Frozen shortlist for code-level study

- `KainosSoftwareLtd/VRSceneOverlay`
- `artumino/SteamVR_HUDCenter`
- `LapisGit/LapisOverlay`
- `elvissteinjr/SteamVR-PrimaryDesktopOverlay`
- `Martin-Oehler/SteamVR-WebApps`
- `hai-vr/h-view`
- `LunarG/OpenXR-Overlays-UE4-Plugin`

## Secondary candidates discovered in the same wave

- `Denwa/vive-wireless-info-overlay`
- `vrkit-platform/vrkit-platform`

## Execution model

### Step 1: Search and deduplicate

- search GitHub by `overlay family` and `host model`, not by generic XR
  keywords only;
- compare every candidate against `catalog/project-registry.md`;
- reject already-covered repos unless the current note is too shallow or the
  repo adds a meaningfully different overlay-host pattern.

### Step 2: Freeze the shortlist

- keep the wave bounded around `overlay-first hosts`, `HUD micro-overlays`,
  `web-backed overlays`, and `scene or engine overlay scaffolds`;
- prefer repos that demonstrate a reusable UI-transport or overlay-lifecycle
  boundary instead of only one narrow end-user feature.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep cloned sources local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- README and actual product framing;
- whether it is a `library`, `overlay host`, `micro-tool`, or `engine plugin`;
- how the overlay is created and updated;
- which UI stack is reused;
- how input is translated back into the UI;
- settings, persistence, and auto-launch behavior;
- whether the repo is a `real donor`, a `product reference`, or mostly a
  `comparison node`.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 15 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave sharpens reusable
  overlay-host, UI-rasterization, scene-overlay, and overlay-patching methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- repository structure and navigation remain coherent;
- newly studied repositories land in the correct registry and overlap families;
- follow-up backlog stays honest about `source-light` repos versus true donors;
- `.research-sources/` remains ignored by git;
- no local-only source clones are accidentally vendored into the public repo.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 15 synthesis document exists with code-level findings;
4. newly studied repositories are promoted into the registry and families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
