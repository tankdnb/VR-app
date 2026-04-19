# GitHub Research Wave 37 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `mixed-VR controller bridges`, `driver-side input emulation`, and
  `hand-tracking to controller adaptation`.

## Why this wave exists

The repository already contained tracker bridges, custom-device drivers, and
some mixed-runtime hardware work, but it still lacked a tighter comparison
around `controller-side bridge design`:

- drivers that reuse foreign runtime data to expose usable SteamVR controllers;
- IPC bridges that let an external process spawn or drive synthetic devices;
- hand-tracking repos that try to emulate full controllers rather than only
  expose finger data.

This wave exists to make `mixed-VR controller bridge design` clearer inside
`VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- Oculus Touch mixed-VR bridges;
- OpenHMD-based controller and HMD bridges into SteamVR;
- IPC-driven controller-emulation drivers;
- hand-tracking-to-controller emulation repos for Quest and other foreign
  sources.

## Frozen shortlist for code-level study

- `mm0zct/Oculus_Touch_Steam_Link`
- `ChristophHaag/SteamVR-OpenHMD`
- `kodowiec/Yet-Another-OpenVR-IPC-Driver`
- `bdub1011/Quest-Link-Hand-Tracking`

## Secondary candidates surfaced in the same wave

- `mSparks43/PSVR-SteamVR-openHMD`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for mixed-VR controller drivers, OpenHMD bridges, IPC driver
  bridges, and hand-tracking controller emulators;
- compare results against `catalog/project-registry.md`;
- reject repos that only duplicate tracker ingress without adding a real
  controller-side or mixed-runtime lesson.

### Step 2: Freeze the shortlist

- keep the wave centered on `controller and hand-input adaptation`, not on
  generic tracker bridges;
- allow both mature bridges and thinner experimental repos so the family stays
  comparative.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where controller properties, input profiles, and device roles are declared;
- whether foreign runtime data is read in-process, via IPC, or through a
  helper;
- whether the reusable lesson is `mixed-VR bridge`, `IPC device bridge`, or
  `gesture-configurable hand emulation`.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 37 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` for honest thin-source or comparison
  nodes;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies
  controller-emulation methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `mixed-VR controller bridges` stay distinct from generic tracker ingress;
- the family clearly separates mature bridges, generic IPC driver bridges, and
  thinner gesture-emulation repos;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 37 synthesis document exists with code-level findings;
4. the registry and families clearly represent mixed-VR controller bridges and
   driver-side input emulation;
5. controller-bridge methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
