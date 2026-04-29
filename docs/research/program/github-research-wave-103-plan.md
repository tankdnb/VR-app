# GitHub Research Wave 103 Plan

- Date: `2026-04-30`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat avatar text`, `speech`, `translation`, and `viseme sidecars`.

## Why this wave exists

`VR-apps-lab` already had thinner text-surface and STT coverage, but it needed
stronger coverage of the branch where
`speech or translation becomes avatar-visible output, visemes, or overlay-fed
communication surfaces`.

This wave exists to make the `avatar-facing speech and text sidecar` branch
clearer.

## Search scope

Primary search directions for this wave:

- TTS or translation hubs with VRChat OSC output;
- avatar-facing speech sidecars with viseme or lip-sync support;
- overlay-backed translation or caption surfaces;
- prefab or product references for speech bubbles built over avatar-text
  substrate.

## Frozen shortlist for code-level study

- `VRCWizard/TTS-Voice-Wizard`
- `YusufOzmen01/kikitan-translator`
- `met4citizen/HeadTTS`
- `Frosty704/Billboard`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `yum-food/TaSTT`
  was already tracked and remained useful mainly as an overlap comparison node;
- `killfrenzy96/KillFrenzyAvatarText`
  stayed a lineage anchor rather than the best new deep-pass target for this
  wave;
- `I5UCC/VRCTextboxSTT`
  was already tracked and mattered here mostly as a downstream integration
  node.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for avatar text, TTS, translation, overlay subtitle, and
  viseme-output queries;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where speech, translation, OSC, overlay, or lip-sync flow is
  visible in source.

### Step 2: Freeze the shortlist

- keep the wave centered on
  `avatar-facing speech and text surfaces`
  rather than all communication tools;
- allow one prefab-heavy product reference if it exposes strong product and UX
  lessons even when code visibility is thinner.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the main value is speech orchestration, translation, TTS substrate,
  or avatar-visible surface design;
- where queueing, OSC fan-out, overlay control, or viseme timing actually
  lives;
- which repos are strong code donors and which remain better product
  references.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 103 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- avatar text and speech sidecars are represented as a distinct family rather
  than a leftover of generic chatbox tooling;
- code donors and prefab-heavy references stay classified honestly;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 103 synthesis document exists with code-level findings;
4. the registry and families represent avatar-facing speech and text donors
   more clearly;
5. new methods are captured where this wave clarified TTS, viseme, translation,
   overlay, or speech-surface patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
