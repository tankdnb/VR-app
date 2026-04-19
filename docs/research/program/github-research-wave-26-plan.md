# GitHub Research Wave 26 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `vendor IPC ecosystems`, `glasses bridges`, and
  `official-stack enhancement tools`.

## Why this wave exists

The repository already had one strong signal in `PSVR2Toolkit`, but the family
was still incomplete:

- the downstream IPC consumers were not mapped;
- vendor enhancement tooling and configuration micro-tools were under-described;
- glasses bridges were present but still only partially integrated;
- the repo still needed a cleaner comparison between
  `vendor wrapper`, `consumer module`, `config helper`, and
  `SDK-first bridge`.

This wave exists to make `vendor and glasses ecosystems` a stronger product and
architecture direction inside `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- PSVR2-related tooling that extends an official stack without replacing it;
- downstream modules and utilities built on a local vendor IPC contract;
- AR/XR glasses bridges that expose SDK plus driver splits;
- custom-hardware bridges that emulate several SteamVR device roles from one
  sidecar.

## Frozen shortlist for code-level study

- `BnuuySolutions/PSVR2Toolkit`
- `BnuuySolutions/PSVR2Toolkit.VRCFT`
- `s-ilent/PSVR2ToolkitTriggerConfig`
- `tabithamoon/ResonitePSVR2`
- `verncat/RayNeo-Air-3S-Pro-OpenVR`
- `verncat/RayNeo-Air-3S-Pro-OpenVR-Driver`
- `DaniXmir/GlassVr`

## Secondary candidates surfaced in the same wave

- `BnuuySolutions/PSVR2Toolkit-Lite`
- `tobexeon/PSVR2EyeTrackingCalibration`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for `PSVR2Toolkit`, `PSVR2 eye tracking`, `RayNeo OpenVR`,
  `glasses SteamVR driver`, and related enhancement-tool queries;
- compare results against `catalog/project-registry.md`;
- reject weak forks unless they expose a new IPC consumer, config helper, or
  dedicated driver split.

### Step 2: Freeze the shortlist

- keep the wave centered on `official-stack enhancement` and
  `glasses or custom-display bridges`;
- allow narrow downstream modules when they teach a reusable ecosystem lesson.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- whether the main boundary is `vendor hook`, `local IPC`, `consumer module`,
  `SDK`, or `device-emulation sidecar`;
- how configuration, calibration, and downstream consumption work;
- whether the repo is a major donor, a downstream ecosystem node, or a
  variant-only signal.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 26 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies vendor IPC
  and enhancement-ecosystem methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `vendor wrapper`, `consumer module`, and `config helper` stay clearly
  separated instead of collapsing into one toolkit bullet;
- glasses bridges land in the right overlap family with their driver splits
  visible;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 26 synthesis document exists with code-level findings;
4. newly clarified vendor-enhancement and glasses repos are promoted or
   reclassified in the registry and families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
