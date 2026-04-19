# GitHub Research Wave 12 Plan

- Date: `2026-04-19`
- Goal: run the next serious GitHub research wave for repositories not yet
  represented in `VR-apps-lab`, focusing on synthetic devices,
  input-emulation sidecars, DIY/custom-hardware drivers, and
  motion-manipulation paths around `SteamVR/OpenVR`.

## Why this wave exists

After Wave 11, the repository had stronger coverage of:

- runtime adapters and OpenXR bring-up helpers;
- virtual-display and repurposed-output drivers;
- workflow micro-utilities and validation tools;
- small driver tutorials and synthetic-controller examples.

What was still underrepresented were:

- `legacy and niche hardware bridge drivers` that recover or repurpose unusual
  peripherals for SteamVR;
- `sample-derived custom-device paths` that stay smaller than a full hardware
  product stack;
- `input-emulation sidecars` that piggyback on existing tracked devices instead
  of building a whole new driver end to end;
- `pose-manipulation drivers` that rewrite or compensate tracking at the driver
  boundary;
- `DIY controller and HMD experiments` that expose practical low-cost
  prototyping techniques.

## Search scope

Primary search directions for this wave:

- SteamVR/OpenVR custom controller and synthetic-device drivers
- legacy peripheral bridge drivers
- DIY HMD and controller paths
- InputEmulator-based sidecars and hybrid device helpers
- motion compensation and pose-rewrite drivers

## Frozen shortlist for code-level study

- `ValveSoftware/driver_hydra`
- `alatnet/OpenPSVR`
- `r57zone/OpenVR-driver-for-DIY`
- `gpsnmeajp/SegsVRControllerDriverSample`
- `puresoul/Barebone`
- `mmorselli/Joy2OpenVR`
- `mdovgialo/SteamVR-Glove`
- `openvrmc/OpenVR-MotionCompensation`

## Secondary candidate discovered in the same wave

- `verncat/RayNeo-Air-3S-Pro-OpenVR`

## Execution model

### Step 1: Search and deduplicate

- search GitHub with focused `gh search repos` queries and topic streams;
- compare candidates against `catalog/project-registry.md`;
- reject repos already covered in earlier waves, shallow forks, and generic XR
  engines with no direct utility or driver-plumbing value.

### Step 2: Freeze the shortlist

- keep the wave bounded around one coherent family;
- prefer repositories that add a new bridge pattern, synthetic-device method,
  or hardware adaptation technique.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep cloned sources local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- README and device/workflow intent;
- driver, helper-app, client, or sidecar split;
- how inputs, poses, or calibration data reach SteamVR;
- whether the project uses a full driver, a sample-derived driver, or an
  InputEmulator-style sidecar;
- packaging, install, and runtime assumptions that affect reuse.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 12 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where the wave sharpens reusable
  device-side methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- repository structure and navigation remain coherent;
- newly added projects land in the correct registry section and family;
- follow-up backlog stays honest about partially studied entries;
- `.research-sources/` remains ignored by git;
- no local-only source clones are accidentally vendored into the public repo.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 12 synthesis document exists with code-level findings;
4. newly studied repositories are promoted into the registry and overlap
   families;
5. newly exposed follow-up gaps are added to the deep-study backlog;
6. methods and navigation are updated where justified;
7. the result is reviewed and pushed to GitHub.
