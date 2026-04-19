# GitHub Research Wave 13 Plan

- Date: `2026-04-19`
- Goal: run the next serious GitHub research wave for repositories not yet
  represented in `VR-apps-lab`, focusing on `vision-based tracking`,
  `camera-driven hand/body bridges`, and `headsetless camera runtimes` across
  `SteamVR/OpenVR` and `OpenXR`.

## Why this wave exists

After Wave 12, the repository had stronger coverage of:

- synthetic devices and sample-derived controller drivers;
- DIY/custom-hardware OpenVR paths;
- input-emulation sidecars and pose-rewrite drivers;
- classic tracker bridges, OSC tools, and headsetless null-driver workflows.

What was still underrepresented were:

- `service-backed hand drivers` that wrap vendor or foreign-runtime hand
  tracking into SteamVR controllers;
- `camera CV sidecars` that estimate body or hand pose and then choose between
  SteamVR-driver and OSC output paths;
- `modular body-tracking platforms` that host swappable device plugins and
  output-service endpoints;
- `headsetless camera runtimes` that go beyond a null driver and implement a
  real runtime-facing substitute.

## Search scope

Primary search directions for this wave:

- SteamVR/OpenVR hand-tracking drivers
- Quest/OpenXR hand-tracking bridges into SteamVR
- webcam and camera-based full-body tracking paths
- Kinect and low-cost tracking platforms with modern plugin models
- OpenXR runtimes that use a webcam instead of dedicated VR hardware

## Frozen shortlist for code-level study

- `ultraleap/driver_ultraleap`
- `Nordskog/HandOfLesser`
- `NovaAshwolfDev/HandCameraDriver`
- `KinectToVR/KinectToVR`
- `KinectToVR/Amethyst`
- `ju1ce/Mediapipe-VR-Fullbody-Tracking`
- `Wunder-Wulfe/NVIDIA-BodyTracking`
- `chnoblouch/aethervr`

## Secondary candidates discovered in the same wave

- `ju1ce/Simple-OpenVR-Bridge-Driver`
- `MasonSakai/VR-AI-Full-Body-Tracking`

## Execution model

### Step 1: Search and deduplicate

- search GitHub by family and workflow type, not by generic XR keywords only;
- compare candidates against `catalog/project-registry.md`;
- reject repos already covered in earlier waves, generic CV demos with no VR
  bridge, and very thin wrappers that add no new pattern.

### Step 2: Freeze the shortlist

- keep the wave bounded around `vision-driven tracking and runtime
  substitution`;
- prefer repositories that expose a new transport split, tracking pipeline,
  plugin boundary, or runtime-registration pattern.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep cloned sources local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- README and actual workflow intent;
- driver, service, sidecar, or runtime split;
- pose, gesture, or tracker transport model;
- calibration, offset, and settings flow;
- whether the project is a mature bridge, a platform shell, or a WIP proof of
  concept.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 13 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where the wave sharpens reusable
  tracking and runtime methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- repository structure and navigation remain coherent;
- newly added projects land in the correct registry sections and overlap
  families;
- follow-up backlog stays honest about partially studied entries;
- `.research-sources/` remains ignored by git;
- no local-only source clones are accidentally vendored into the public repo.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 13 synthesis document exists with code-level findings;
4. newly studied repositories are promoted into the registry and overlap
   families;
5. newly exposed follow-up gaps are added to the deep-study backlog;
6. methods and navigation are updated where justified;
7. the result is reviewed and pushed to GitHub.
