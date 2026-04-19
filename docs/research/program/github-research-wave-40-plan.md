# GitHub Research Wave 40 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `VRChat chatbox workflows`, `speech-to-text sidecars`, and
  `avatar text-surface utilities`.

## Why this wave exists

The repository already had communication helpers, captions, and some
VRChat-facing utilities, but one branch was still too diffuse:

- chatbox composers that pack several live status sources into one bounded text
  surface;
- speech-to-avatar text pipelines that render text through animator or
  parameter grids rather than a plain overlay;
- keyboard or textbox micro-utilities that make chat entry possible from inside
  existing VR overlay surfaces.

This wave exists to make `VRChat chatbox, STT, and text-surface sidecars`
clearer inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- VRChat chatbox utilities and `OSC`-driven textbox apps;
- speech-to-text sidecars that target avatar text rendering or chatbox output;
- overlay keyboard patches and non-native typing paths for chat entry;
- broad status composers that treat the chatbox as a compact utility surface.

## Frozen shortlist for code-level study

- `BoiHanny/vrcosc-magicchatbox`
- `yum-food/TaSTT`
- `cyberkitsune/vrc-osc-scripts`
- `nyakowint/xsoverlay-keyboard-osc`
- `I5UCC/VRCTextboxOSC`
- `Lioncat6/OSC-Chat-Tools`

## Secondary candidates surfaced in the same wave

- `I5UCC/VRCTextboxSTT`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for VRChat chatbox, STT, textbox, and overlay-keyboard tools;
- compare results against `catalog/project-registry.md`;
- reject repos that duplicate a thinner textbox or chat helper without adding a
  new text-surface, STT, or overlay-entry lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `text surfaces and chat entry`, not generic social
  overlays alone;
- allow both broad status-composer apps and very thin textbox micro-utilities
  so the family stays comparative.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how text gets generated, trimmed, paged, or rate-limited;
- whether the output target is the chatbox, avatar parameters, or an existing
  keyboard surface;
- where settings, hotkeys, and desktop-to-VR boundaries live.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 40 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest follow-up nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies
  chatbox-sidecar and text-surface methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `chatbox and text-surface sidecars` stay distinct from generic captions or
  broader communication overlays;
- the family clearly separates broad composers, avatar text renderers,
  micro-scripts, and overlay-entry helpers;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 40 synthesis document exists with code-level findings;
4. the registry and families clearly represent VRChat chatbox and text-surface
   sidecars;
5. chatbox and text-surface methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
