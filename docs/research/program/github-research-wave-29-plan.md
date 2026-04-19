# GitHub Research Wave 29 Plan

- Date: `2026-04-19`
- Goal: run the next focused GitHub research wave for repositories that were
  still underrepresented in `VR-apps-lab`, focusing on
  `hand menus`, `palm menus`, `radial menus`, and `quick-access VR surfaces`.

## Why this wave exists

The repository already contained many overlays and tool windows, but it still
needed a cleaner synthesis around `how a user opens commands in VR quickly`:

- palm-up launchers versus wrist or floating menus;
- radial selection versus richer world-space panels;
- editor-generated menu scaffolds versus runtime-only menu logic.

This wave exists to make `VR menu activation and quick-access surfaces` a
stronger family in `VR-apps-lab`.

## Search scope

Primary search directions for this wave:

- hand-menu and palm-menu samples;
- radial, ring, and quick-access VR menus;
- menu-generation toolkits;
- contextual secondary-panel flows for XR UI.

## Frozen shortlist for code-level study

- `NovaUI-Unity/XRHandMenuSample`
- `Housz/VRMenuDesigner`
- `Oyshoboy/RadialMenuVR`
- `yusufalibrahim1994/UnityXR-Physicalized-Radial-Menu`
- `auroreRakoto/XR-UI-Prototype`

## Execution model

### Step 1: Search and deduplicate

- search GitHub for hand menu, palm menu, radial menu, XR quick menu, and VR
  menu toolkit queries;
- compare results against `catalog/project-registry.md`;
- reject repos that only show finished art direction without reusable control
  or menu behavior.

### Step 2: Freeze the shortlist

- keep the wave centered on `menu activation and selection patterns`;
- include both `utility menu` and `framework-like scaffold` projects so the
  family reflects multiple construction paths.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- how the menu is revealed and hidden;
- whether the user points, scrolls, hovers, or grabs to select;
- whether the project is a one-off menu or a reusable menu-generation scaffold.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 29 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md` if honest follow-up nodes remain;
- `methods/vr-utility-methods-catalog.md` where this wave clarifies menu and
  quick-access interaction methods.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- `palm-up launchers` stay distinct from `radial selection` and
  `context-panel` flows;
- menu-generation toolkits stay separated from tiny scene demos;
- `.research-sources/` stays ignored by git;
- documentation indexes link to the new wave cleanly.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 29 synthesis document exists with code-level findings;
4. the registry and families clearly represent VR quick-access menu donors;
5. menu-oriented methods are added where justified;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
