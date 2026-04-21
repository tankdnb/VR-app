# GitHub Research Wave 92 Plan

- Date: `2026-04-21`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat world persistence`, `inventory helpers`, `save-manager companions`,
  and `external-data bridges`.

## Why this wave exists

`VR-apps-lab` already had better coverage of creator-facing video, audio, and
world utility surfaces than of `how creator worlds persist data or escape
platform limitations when they need save state, inventory state, or external
web access`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- VRChat world save-state systems;
- creator-world inventory and holster utilities;
- world-specific save-manager companions;
- external helper processes that bridge Udon to HTTP, WebSocket, or local
  storage without client mods.

## Frozen shortlist for code-level study

- `Nestorboy/NUSaveState`
- `ChrisFeline/ToNSaveManager`
- `TealOrangeCat/InventorySystem`
- `DarthShader/Udon-MIDI-Web-Helper`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `tutinoco/SimpleNetwork` and `DeltaNeverUsed/UdonSharpNetworkingLib`
  stayed outside this wave because the main focus here is persistence and
  external-data boundaries, not generic message transport;
- `Reava/UwUtils`
  stayed outside this wave because it is broader creator utility substrate and
  fits better in a utility-library wave than in a persistence-centered one.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for VRChat persistence, inventory, and external-data helper
  projects;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where state storage or bridge boundaries are visible in source.

### Step 2: Freeze the shortlist

- keep the wave centered on `world persistence and external data`, not on every
  creator-side utility repo;
- allow both in-world systems and out-of-world companion apps when they clarify
  different persistence or bridge patterns.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where save-state or inventory ownership is represented;
- whether persistence lives fully inside the world, outside the world, or in a
  bridge between the two;
- how logs, OSC, MIDI, or WebSocket paths are used as transport;
- what reusable persistence or bridge methods belong in the methods catalog.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 92 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- in-world persistence stays distinct from out-of-world log or helper flows;
- specific world save companions are described honestly as product references
  when their donor value is narrower than their product framing;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 92 synthesis document exists with code-level findings;
4. the registry and families represent creator-world persistence and
   bridge patterns more clearly;
5. new methods are captured where this wave clarified reusable persistence or
   transport ideas;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
