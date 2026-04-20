# GitHub Research Wave 79 Plan

- Date: `2026-04-20`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `desktop-window overlay shells`, `Linux capture utilities`, and
  `launcher stubs`.

## Why this wave exists

`VR-apps-lab` already had strong coverage of overlay hosts, dashboard shells,
and Linux desktop-in-VR ecosystems, but it still lacked a cleaner map of the
small and sometimes awkward repos that show:

- native desktop capture routed into an overlay surface;
- command-first overlay control rather than GUI-first shells;
- launcher-style or product-direction repos that matter conceptually even when
  public source is thin.

This wave exists to make those edges visible without pretending they are all
equally mature.

## Search scope

Primary search directions for this wave:

- desktop capture overlays built on OpenVR or SteamVR;
- Linux overlay tools for portal or PipeWire window capture;
- narrow launcher or overlay starter repos around desktop visibility in VR.

## Frozen shortlist for code-level study

- `ShiraoShotaro/DesktopOverlayer`
- `nyxpirientity/ovr-penguin`
- `gamenew09/RobloxVRLauncher`

## Secondary candidates surfaced in the same wave

These candidates overlapped with already-tracked families strongly enough that
they did not justify widening this wave:

- `CircuitLord/DesktopPortal`
- `rhaamo/OpenVR-Display-Devices`
- `fnuidesktop-VR`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for desktop overlays, desktop capture shells, and small
  launcher repos;
- compare results against `catalog/project-registry.md`;
- prefer repos that expose a distinct capture or shell boundary rather than
  another large desktop-in-VR platform.

### Step 2: Freeze the shortlist

- keep the wave centered on `desktop window surfaces and shell shape`;
- allow one thin launcher placeholder when it helps document a product branch
  that otherwise stays easy to miss.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how window or screen capture is acquired and routed into overlay textures;
- whether the shell is GUI-first, CLI-first, or only a public placeholder;
- how transforms, input, overlay parenting, and saved state are exposed;
- whether the repo is strongest as a code donor, product reference, or follow-up
  stub.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 79 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- capture-backed overlay shells stay distinct from larger desktop-in-VR hosts;
- public placeholder repos are described honestly;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 79 synthesis document exists with code-level findings;
4. the registry and families represent these desktop-window overlay donors more
   clearly;
5. new methods are captured where this wave clarified reusable patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
