# GitHub Research Wave 18 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `low-level OpenVR driver learning paths`, `custom-device providers`, and
  `DIY or repurposed display bridges`.

## Why this wave exists

After Waves 12 through 17 the repository had a growing set of device-side
references, but the learning path was still uneven:

- some repos were `full products` and hard to learn from quickly;
- some were `sample-like`, but not yet normalized into the later-wave style;
- some mixed a driver with a sidecar, overlay, or hardware SDK and therefore
  taught more about architecture than about raw API calls.

This wave exists to clarify the strongest `driver-side learning track` in the
repo.

## Search scope

Primary search directions for this wave:

- OpenVR driver tutorials and sample-derived repos;
- custom-device providers with multiple transport options;
- DIY HMD and repurposed-display paths;
- AR glasses or nonstandard hardware bridged into SteamVR/OpenVR;
- driver-side repos that pair a runtime component with an external config or
  sidecar app.

## Frozen shortlist for code-level study

- `terminal29/Simple-OpenVR-Driver-Tutorial`
- `LucidVR/opengloves-driver`
- `TrueOpenVR/SteamVR-TrueOpenVR`
- `DaniXmir/GlassVr`
- `r57zone/OpenVR-ArduinoHMD`

## Execution model

### Step 1: Search and deduplicate

- search by `driver learning role` and `hardware bridge role`;
- compare every candidate against `catalog/project-registry.md`;
- reject duplicates unless the repo exposes a new device model, sidecar split,
  or configuration pattern.

### Step 2: Freeze the shortlist

- keep the wave bounded around `learning path`, `device provider`,
  `repurposed display`, and `DIY HMD` ideas;
- prefer repos that reveal a reusable driver boundary rather than only a niche
  hardware target.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- README and actual hardware or product framing;
- how devices are created and registered;
- whether the repo is `sample-derived`, `modular`, or `bridge-like`;
- config, transport, and sidecar boundaries;
- what remains reusable even if the target hardware itself is niche.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 18 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave sharpens
  multi-transport device-provider and repurposed-display patterns.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- driver-family placement remains coherent;
- sample-derived repos are distinguished from full products and hardware
  bridges;
- partially exhausted large repos remain labeled honestly;
- `.research-sources/` stays ignored by git.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 18 synthesis document exists with code-level findings;
4. newly studied repos are promoted or reclassified in the registry and
   families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
