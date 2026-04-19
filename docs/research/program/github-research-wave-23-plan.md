# GitHub Research Wave 23 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `glove platforms`, `poser stacks`, and `nonstandard hardware bridge drivers`.

## Why this wave exists

The repository already had strong coverage of:

- driver tutorials and sample-derived custom-device paths;
- vendor enhancements and repurposed-display bridges;
- tracker bridges and camera-based tracking stacks.

What still needed a tighter pass was the hardware family where:

- a `custom device ecosystem` spans firmware, protocol, sidecar, and driver;
- a driver is fed by an explicit external `poser` or `binding` API instead of
  only by a private service;
- unusual physical devices or foreign tracking stacks become SteamVR devices
  through a bridge layer.

This wave exists to strengthen the repo's `custom hardware and bridge-driver`
learning track with richer modern examples than the earlier tutorial-heavy
coverage alone.

## Search scope

Primary search directions for this wave:

- glove ecosystems with both firmware and SteamVR driver surfaces;
- driver stacks that expose an external protocol or language bindings;
- unusual physical-control bridges such as cockpit, Hydra, or remote-tracker
  relays;
- compatibility bridges for foreign VR frameworks that still teach useful
  architectural lessons.

## Frozen shortlist for code-level study

- `LucidVR/opengloves-driver`
- `LucidVR/lucidgloves`
- `HoboVR-Labs/hobo_vr`
- `Copprhead/hotas-vr-controller`
- `SophiaH67/soph_wireless`
- `SophiaH67/soph_wireless_transmitter`
- `OSVR/SteamVR-OSVR`
- `terminal29/OSVR-SteamVR-Bridge`
- `r57zone/Razer-Hydra-SteamVR-driver`

## Secondary candidates surfaced in the same wave

- `puresoul/Barebone`
- `TrueOpenVR/SteamVR-TrueOpenVR`

## Execution model

### Step 1: Search and deduplicate

- search GitHub by `glove driver`, `SteamVR poser`, `remote tracker relay`,
  `OSVR SteamVR`, and `Hydra SteamVR` family queries;
- compare candidates against `catalog/project-registry.md`;
- reject thin forks unless they expose a new protocol, hardware split, or
  bridge pattern.

### Step 2: Freeze the shortlist

- keep the wave centered on `custom hardware ecosystems` and
  `external-protocol-driven drivers`;
- allow legacy bridges only when they teach a still-useful compatibility or
  peripheral-integration lesson.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- firmware, transport, and driver boundaries;
- whether the repo exposes a public protocol, poser, binding, or sidecar API;
- how the driver shell stays stable while operational logic moves outside it;
- whether the repo is a true donor, a historical reference, or a comparison
  node only.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 23 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave sharpens glove,
  poser, and custom-hardware ecosystem methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- hardware bridges land in the right family instead of blending into generic
  tracker-bridge notes;
- firmware-plus-driver ecosystems remain described as ecosystems, not as single
  binaries;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 23 synthesis document exists with code-level findings;
4. newly clarified hardware and bridge-driver repos are promoted or reclassified
   in the registry and families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
