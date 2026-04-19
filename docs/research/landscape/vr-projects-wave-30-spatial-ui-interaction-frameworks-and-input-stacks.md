# VR Projects Wave 30: Spatial UI Interaction Frameworks and Input Stacks

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `spatial UI interaction frameworks`, `input stacks`, and
  `menu-enabling XR scaffolds`.

## Why this wave exists

The repository already had small menu and keyboard donors, but it still needed
stronger references for the framework layer that explains how those surfaces
become usable at all:

- how to adapt a 2D UI event system into VR ray, poke, and hand interaction;
- how hand menus are gated by palm orientation, gaze, or gesture heuristics;
- how a toolkit packages keyboard, panel, and world-space UI patterns into a
  reusable stack.

This wave exists to make `XR UI plumbing` a clearer donor family in
`VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with XR interaction toolkit, mixed reality toolkit UI, 3D UI
   input module, and hand-menu framework queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `Unity-Technologies/XR-Interaction-Toolkit-Examples` | Strongest combined sample set for spatial keyboard, 2D UI, 3D UI, gaze, and world-space interaction |
| `microsoft/MixedRealityToolkit-Unity` | Strongest legacy donor for palm-up hand-menu solvers and broad spatial UI primitives |
| `ViveSoftware/ViveInputUtility-Unity` | Best donor for adapting Unity UI to VR pointers through a dedicated 3D input module |
| `Unity-Technologies/mr-example-meta-openxr` | Strong Meta/OpenXR-side sample for hand menus, panel manipulation, and gesture-gated spatial UI |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `MixedRealityToolkit/MixedRealityToolkit-Unity` | Important current-generation continuation of the MRTK line, but this pass centered on the better-known legacy donor and framework comparisons already visible in the main shortlist |
| `oculus-samples/Unity-FirstHand` | Strong adjacent hand-interaction sample, but this wave already had stronger donors for reusable UI plumbing and menu scaffolding |

## Deep-pass notes by project

## `Unity-Technologies/XR-Interaction-Toolkit-Examples`

- GitHub:
  [Unity-Technologies/XR-Interaction-Toolkit-Examples](https://github.com/Unity-Technologies/XR-Interaction-Toolkit-Examples)
- What it is:
  a broad sample repository for Unity's XR Interaction Toolkit, including
  spatial keyboard, 2D UI, 3D UI, gaze, and interactor patterns.
- Why it matters:
  it is the strongest combined donor in the repo for
  `general-purpose spatial UI stack with keyboard and panel samples`.
- Interesting ideas:
  keep keyboard, gaze, panel, and UI-interaction samples in one coherent
  toolkit surface; expose keyboard focus, submission, layout, and modifier
  state as part of the XR UI sample stack; show how 2D and 3D UI patterns live
  under one interaction system.
- Interesting implementation choices:
  `XRKeyboard.cs`, `XRKeyboardConfig.cs`, `XRKeyboardLayout.cs`,
  `XRKeyboardDisplay.cs`, and the broader sample stations make the toolkit-wide
  `UI plus input` model easy to inspect.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  large sample repository, so it teaches many overlapping things at once.
- What to inspect next:
  keep it as the main baseline for future comparisons involving `spatial
  keyboard inside a larger XR toolkit`.

## `microsoft/MixedRealityToolkit-Unity`

- GitHub:
  [microsoft/MixedRealityToolkit-Unity](https://github.com/microsoft/MixedRealityToolkit-Unity)
- What it is:
  the legacy MRTK repository with a broad library of spatial UI primitives,
  hand menus, solvers, and non-native keyboard support.
- Why it matters:
  it is the strongest donor in the repo for
  `solver-driven hand-menu activation and broad spatial UI prefab systems`.
- Interesting ideas:
  gate hand menus by palm orientation and optional flat-hand rules; pair
  hand-menu placement with camera-facing heuristics; use a large prefab library
  for sliders, dialogs, object collections, near menus, and pressable buttons.
- Interesting implementation choices:
  `HandConstraintPalmUp.cs` makes palm, gaze, and follow-hand logic explicit,
  while `NonNativeKeyboardTouchAssistant.cs` shows how articulated-hand support
  is grafted onto keyboard interaction.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  a legacy toolkit line, so future passes should keep the successor repo in
  view without collapsing the distinction.
- What to inspect next:
  revisit its continuation line separately, but keep this repo as the main
  baseline for `solver and prefab` style spatial UI design.

## `ViveSoftware/ViveInputUtility-Unity`

- GitHub:
  [ViveSoftware/ViveInputUtility-Unity](https://github.com/ViveSoftware/ViveInputUtility-Unity)
- What it is:
  an HTC-oriented Unity utility stack that includes role-based input, hand
  tracking, teleport, and a dedicated 3D UI pointer system.
- Why it matters:
  it is the strongest donor in the repo for
  `VR-aware UI input module and custom raycaster stack`.
- Interesting ideas:
  adapt Unity's EventSystem instead of replacing it wholesale; support 3D
  pointer raycasters and hand interaction; keep role binding and pointer logic
  reusable across platform variants.
- Interesting implementation choices:
  `Pointer3DInputModule.cs`, `CanvasRaycastMethod.cs`,
  `Pointer3DRaycaster.cs`, and `ViveRaycaster.cs` make the `VR pointer ->
  EventSystem` adaptation layer very visible.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  broader than UI alone, so only part of the repo belongs directly to this
  family.
- What to inspect next:
  compare it with MRTK and XRIT whenever a future prototype needs to decide
  whether to extend an existing UI system or replace it.

## `Unity-Technologies/mr-example-meta-openxr`

- GitHub:
  [Unity-Technologies/mr-example-meta-openxr](https://github.com/Unity-Technologies/mr-example-meta-openxr)
- What it is:
  a Meta/OpenXR sample stack for spatial UI, hand menus, panel manipulation,
  and MR interaction scaffolds.
- Why it matters:
  it is the strongest donor in the repo for
  `runtime-vendor sample stack with hand-menu and spatial-panel scaffolding`.
- Interesting ideas:
  expose hand-menu setup as a reusable prefab pattern; combine lazy-follow
  panels, spatial scroll surfaces, onboarding panels, and gesture gating in one
  example app; treat system gestures as menu-state signals.
- Interesting implementation choices:
  `MetaSystemGestureDetector.cs`, `Hand Menu Setup` prefabs, and `Spatial Panel
  Scroll` surfaces make the `gesture -> menu/panel` flow easy to study.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  more vendor-shaped than the broader toolkit donors.
- What to inspect next:
  use it whenever a future wave needs a practical reference for
  `modern palm-menu and panel-manipulation UX` in a Meta/OpenXR context.

## Main takeaways from Wave 30

- The strongest framework split in this family is:
  - `sample toolkit with integrated keyboard and panel stations`
  - `solver and prefab framework`
  - `UI input-module adaptation layer`
  - `runtime-vendor hand-menu sample stack`
- The most reusable lesson is often not the menu prefab itself, but the
  `activation heuristic` or `EventSystem adaptation` underneath it.
- Framework donors matter because they show how to keep ordinary UI code usable
  in XR without rebuilding every control from scratch.

## Reusable methods clarified by this wave

- `XR UI interaction stack that extends EventSystem with ray, poke, and hand input`

## Recommended next moves after this wave

1. Treat `XR-Interaction-Toolkit-Examples` as the main baseline for
   toolkit-scale XR UI comparison.
2. Keep `MixedRealityToolkit-Unity` visible as the strongest donor for
   `palm-up gating plus solver-driven UI placement`.
3. Use `ViveInputUtility-Unity` as the main donor when a future tool needs a
   focused `pointer and input module` layer rather than a full toolkit.
4. Keep `mr-example-meta-openxr` as the most practical modern comparison for
   `hand-menu plus spatial panel` flows in OpenXR-era Unity samples.
