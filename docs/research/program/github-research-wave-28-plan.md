# GitHub Research Wave 28 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `text entry`, `tracked keyboards`, and `non-native input surfaces`.

## Why this wave exists

The repository already had many overlay and utility references, but it still
needed a stronger synthesis around one practical question:

- how VR tools should handle text entry without falling back to a desktop;
- when a project should use a fully synthetic keyboard versus a tracked
  physical keyboard;
- how keyboard UX changes when the input model is hands, controllers, or a
  runtime-tracked desk device.

This wave exists to make `VR text-entry design` a clearer branch inside
`VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- spatial and non-native keyboards for Unity and XR toolkits;
- tracked physical keyboard samples and passthrough-adjacent keyboard flows;
- hand-tracking keyboard experiments;
- reusable keyboard prefabs, layout systems, and event-driven input surfaces.

## Frozen shortlist for code-level study

- `campfireunion/VRKeys`
- `ultraleap/XR-Keyboard`
- `oculus-samples/Unity-TrackedKeyboard`
- `Ayfel/MRTK-Keyboard`
- `RTUITLab/Oculus-HandTracking-Keyboard`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for VR keyboard, XR keyboard, tracked keyboard, hand-tracking
  keyboard, and non-native keyboard queries;
- compare results against `catalog/project-registry.md`;
- reject repos that are only scene demos unless they still expose a reusable
  input or keyboard pattern.

### Step 2: Freeze the shortlist

- keep the wave centered on `typing and text-entry surfaces`, not generic UI;
- allow a mix of `synthetic`, `tracked physical`, and `hand-driven` keyboards
  so the family stays comparative rather than one-sided.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how the keyboard is spawned, positioned, and dismissed;
- whether layout switching, validation, and submit/cancel events are exposed;
- whether the project acts as a reusable prefab, a toolkit slice, or a product
  sample tied to one runtime feature.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 28 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` if a follow-up node remains honest;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies
  keyboard-oriented utility methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `text-entry surfaces` stay distinguished from broader menu systems;
- tracked hardware keyboards stay separated from purely synthetic keyboards;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 28 synthesis document exists with code-level findings;
4. the registry and families clearly represent VR keyboard and text-entry
   donors;
5. keyboard-oriented methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
