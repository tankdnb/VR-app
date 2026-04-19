# GitHub Research Wave 25 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `headsetless QA runtimes`, `null-driver helpers`, and
  `virtual device simulators`.

## Why this wave exists

The repository already knew about `no-HMD workflows`, but that knowledge was
still split across several unrelated styles:

- manual null-driver recipes;
- one-off virtual HMD drivers;
- full OpenXR runtime simulators;
- camera-driven custom runtimes;
- tiny config-flip utilities.

This wave exists to turn `headsetless development and fake-hardware QA` into a
clear architecture track instead of a pile of workaround notes.

## Search scope

Primary search directions for this wave:

- SteamVR no-headset helpers and null-driver toggles;
- virtual HMD or fake-device drivers for SteamVR;
- OpenXR runtime simulators for desktop bring-up;
- automation-friendly simulator runtimes with GUI or API control surfaces;
- source-light but strategically relevant virtual-display or fake-hardware
  paths.

## Frozen shortlist for code-level study

- `username223/SteamVRNoHeadset`
- `n1ckfg/ViveTrackerExample`
- `oleuzop/VirtualSteamVRDriver`
- `elliotttate/OpenXR-Simulator`
- `shieldmeidunn/SteamVRNullFlipper`
- `OpenDisplayXR/OpenDisplayXR-VDD`
- `chnoblouch/aethervr`
- `ox-runtime/ox-sim-driver`

## Secondary candidates surfaced in the same wave

- `davidrios/openxr-device-simulator`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for `SteamVR no headset`, `OpenXR simulator`, `virtual HMD
  driver`, and `null driver helper` family queries;
- compare results against `catalog/project-registry.md`;
- reject thin duplicates unless they expose a new simulator boundary or a more
  automation-friendly control model.

### Step 2: Freeze the shortlist

- keep the wave centered on `headsetless QA and fake-hardware bring-up`;
- allow tiny workflow repos when they teach a strong config or lifecycle
  lesson.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether it is a manual recipe, a config helper, a driver, a runtime, or a
  simulator platform;
- how runtime registration or driver activation is handled;
- whether the repo exposes a useful automation or external control surface;
- whether it is a true donor, a workflow reference, or a thin comparison node.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 25 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies
  headsetless and simulator construction methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `manual recipe`, `config swapper`, `virtual driver`, and `full runtime`
  patterns stay clearly separated;
- source-light repos stay honestly marked as such;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 25 synthesis document exists with code-level findings;
4. newly clarified headsetless and fake-hardware repos are promoted or
   reclassified in the registry and families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
