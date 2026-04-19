# GitHub Research Wave 24 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `accessibility captions`, `assistive speech surfaces`, and
  `micro-HUD accessibility utilities`.

## Why this wave exists

The repository already had enough accessibility nodes to prove that this is a
real family, not a one-off:

- caption overlays already existed in the registry;
- microphone-state and comfort-status helpers were already present;
- but the family still lacked a modern synthesis that separated
  `native overlay renderers`, `browser-first caption hosts`,
  `game-specific speech hooks`, and `micro-status overlays`.

This wave exists to turn `accessibility overlays` into a first-class product
and method family inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- speech-to-text overlays for SteamVR/OpenVR;
- browser or desktop caption surfaces that can be pulled into VR through an
  existing overlay host;
- game- or app-specific live-caption mods that still teach useful architecture
  lessons;
- microphone and push-to-talk status micro-overlays with a strong assistive
  angle.

## Frozen shortlist for code-level study

- `Vinventive/live-captions-vr`
- `MochiDoesVR/OpenVRCaptions`
- `ctobin1114/UniversalVR-CC`
- `gt0777/VRCLiveCaptionsMod`
- `I5UCC/VRCTextboxSTT`
- `rrazgriz/VRCMicOverlay`
- `matzman666/OpenVR-MicrophoneControl`

## Secondary candidates surfaced in the same wave

- `Beyley/eepyxr`
- `Otter-Co/TurnSignal`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for `SteamVR captions`, `VR live captions`, `OpenVR mic
  overlay`, and related `assistive HUD` queries;
- compare results against `catalog/project-registry.md`;
- reject generic desktop caption tools unless they expose a useful VR-facing
  integration boundary.

### Step 2: Freeze the shortlist

- keep the wave centered on `accessibility surfaces`, not generic utility
  overlays;
- include narrow micro-tools when they demonstrate unusually strong
  accessibility or status-hint UX.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- the speech-recognition or event-ingress boundary;
- whether overlay rendering is native, browser-backed, or delegated to another
  host;
- how settings, persistence, and user-facing configuration work;
- whether the repo is a reusable donor, a UX/product reference, or a
  family-specific comparison node.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 24 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies
  accessibility-overlay construction methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- accessibility repos land in the right family instead of being scattered
  across generic overlay buckets;
- browser-hosted caption tools stay clearly distinguished from native OpenVR
  overlay renderers;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 24 synthesis document exists with code-level findings;
4. newly clarified caption and assistive-HUD repos are promoted or reclassified
   in the registry and families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
