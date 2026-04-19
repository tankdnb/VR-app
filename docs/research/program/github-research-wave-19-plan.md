# GitHub Research Wave 19 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `vendor enhancement tooling`, `repurposed output bridges`, and
  `alternative hardware paths`.

## Why this wave exists

After Wave 18 the repository had a much stronger driver-learning track, but one
important slice still needed consolidation:

- `vendor mods` that augment an official driver instead of replacing it;
- `repurposed display and glasses bridges` that turn nonstandard outputs into
  XR-like hardware paths;
- `alternative hardware paths` where public source quality varies a lot and the
  repo value may be more about product direction than direct donor value.

This wave exists to keep that family honest and structured instead of leaving
it as a broad bucket of exotic hardware repos.

## Search scope

Primary search directions for this wave:

- vendor-enhancement projects that wrap official headset drivers;
- AR glasses and repurposed-display bridges;
- alternative hardware paths that expose an OpenVR driver or SDK boundary;
- virtual hardware driver signals, even when source quality is sparse.

## Frozen shortlist for code-level study

- `BnuuySolutions/PSVR2Toolkit`
- `krazysh01/VirtualDesktop-OpenVR-Trackers`
- `verncat/RayNeo-Air-3S-Pro-OpenVR`
- `alatnet/OpenPSVR`

## Secondary candidate surfaced in the same wave

- `OpenDisplayXR/OpenDisplayXR-VDD`

## Execution model

### Step 1: Search and deduplicate

- search by `vendor enhancement`, `glasses bridge`, and `alternative hardware`
  family tags;
- compare candidates against `catalog/project-registry.md`;
- reject duplicates unless the repo exposes a new wrap-or-augment pattern, SDK
  boundary, or output-bridge angle.

### Step 2: Freeze the shortlist

- keep the wave bounded around `official-driver augmentation`,
  `repurposed-display bridge`, and `alternative hardware path`;
- treat sparse repos honestly instead of forcing them into full donor status.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- README and actual hardware/product framing;
- whether it `wraps`, `replaces`, or `augments` an official stack;
- SDK or driver entry points;
- IPC or service boundaries;
- what remains reusable even if the hardware target is niche or unstable.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 19 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md` where this wave sharpens
  vendor-driver wrapper and repurposed-display methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- vendor-enhancement and hardware-bridge family placement remains coherent;
- source-light repos remain labeled honestly;
- current public snapshots are described as they are now, not as they were once
  expected to be;
- `.research-sources/` stays ignored by git.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 19 synthesis document exists with code-level findings;
4. newly studied repos are promoted or reclassified in the registry and
   families;
5. methods and follow-up backlog are updated where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
