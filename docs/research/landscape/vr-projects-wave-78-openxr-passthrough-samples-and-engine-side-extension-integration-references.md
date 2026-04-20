# VR Projects Wave 78: OpenXR Passthrough Samples and Engine-Side Extension Integration References

- Date: `2026-04-20`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `OpenXR passthrough samples` and
  `engine-side extension integration references`.

## Why this wave exists

`VR-apps-lab` already had useful OpenXR layers and some mixed-reality related
nodes, but it still lacked a cleaner answer to:

`what good engine-facing OpenXR passthrough integration looks like when the goal is a reusable plugin or sample rather than another full product`.

This wave exists to make that family clearer:

- a UE plugin that injects optional passthrough support without a large vendor
  SDK;
- a very small Godot sample that shows the lower bound honestly;
- a broader Unity sample that couples runtime setup, diagnostics, and editor
  helpers.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with OpenXR passthrough and engine-integration queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `AgileLens/ue-openxr-passthrough` | Strong donor for a clean Unreal OpenXR extension plugin that avoids vendor SDK lock-in |
| `BastiaanOlij/godot_test_passthrough` | Strong lower-bound donor for a very small engine-side passthrough toggle |
| `olir/mr-openxr-unity-meta-passthrough-sample` | Useful donor for runtime plus editor passthrough scaffolding inside a Unity sample |

## Deep-pass notes by project

## `AgileLens/ue-openxr-passthrough`

- GitHub:
  [AgileLens/ue-openxr-passthrough](https://github.com/AgileLens/ue-openxr-passthrough)
- What it is:
  a lightweight Unreal Engine plugin that enables Quest Link or Air Link
  passthrough on PCVR by requesting raw OpenXR passthrough extensions without
  taking on the full Meta XR plugin stack.
- Why it matters:
  it is the clearest donor in this wave for
  `engine-native extension plugin without vendor SDK lock-in`.
- Interesting ideas:
  register as an `IOpenXRExtensionPlugin`; request optional extensions and
  degrade cleanly; detect runtime blend-mode limits and adapt engine alpha
  behavior accordingly; expose a runtime toggle without building a huge
  abstraction surface.
- Interesting implementation choices:
  `Source/OpenXRPassthrough/Private/OpenXRPassthrough.cpp`
  wires module startup, optional extension negotiation, function-resolution,
  session hooks, state-event handling, and passthrough layer insertion into the
  engine lifecycle.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  Meta extension specific, but the reusable lesson is really about
  `engine-side extension injection with graceful fallback`.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs an
  `engine plugin that adds one OpenXR feature cleanly`
  donor.

## `BastiaanOlij/godot_test_passthrough`

- GitHub:
  [BastiaanOlij/godot_test_passthrough](https://github.com/BastiaanOlij/godot_test_passthrough)
- What it is:
  a very small Godot sample project that toggles passthrough through the engine
  OpenXR interface and transparent viewport behavior.
- Why it matters:
  it is the clearest lower-bound donor in this wave for
  `minimal engine passthrough toggle`.
- Interesting ideas:
  keep the sample honest and small; expose the essential engine hooks directly;
  couple passthrough enablement with transparent background handling instead of
  hiding the real dependency.
- Interesting implementation choices:
  `avatar/avatar.gd`
  resolves the OpenXR interface, toggles passthrough, and controls viewport
  transparency while the rest of the project stays intentionally small.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  intentionally tiny and tied to a specific engine branch at the time of
  writing, but very useful precisely because the lower bound is obvious.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `small engine-side passthrough sample`
  donor.

## `olir/mr-openxr-unity-meta-passthrough-sample`

- GitHub:
  [olir/mr-openxr-unity-meta-passthrough-sample](https://github.com/olir/mr-openxr-unity-meta-passthrough-sample)
- What it is:
  a Unity sample project that combines runtime passthrough management,
  diagnostics overlays, and editor-time setup helpers for a Meta-focused OpenXR
  passthrough workflow.
- Why it matters:
  it is the clearest donor in this wave for
  `sample project that couples runtime manager and editor bootstrap`.
- Interesting ideas:
  create project setup helpers under `Editor/`; keep runtime passthrough
  management explicit; generate diagnostics overlays at runtime so on-device
  debugging is easier than combing through logs only.
- Interesting implementation choices:
  `Assets/Scripts/XR/PassthroughManager.cs`
  handles runtime component discovery and passthrough initialization,
  `Assets/Scripts/Diagnostics/StatusOverlay.cs`
  creates a small on-screen diagnostics UI, and
  `Assets/Editor/SetupARPassthrough.cs`
  bootstraps scene and project configuration from an editor menu entry.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  broader and more sample-project shaped than the other two repos in this wave,
  so it remains strongest as a scaffolding reference rather than a lower-bound
  donor.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `Unity passthrough setup and diagnostics`
  reference.

## Main takeaways from Wave 78

- `Engine-side OpenXR passthrough donors` now split more cleanly into:
  - `optional extension plugin with runtime-specific adaptation`
  - `very small engine toggle sample`
  - `sample project with editor setup and runtime diagnostics`
- The strongest lesson from this wave is that
  `engine-side extension integration`
  is a distinct donor family from runtime-side API layers.
- Another strong lesson is that the best engine-facing samples make engine
  lifecycle, extension negotiation, scene transparency, and diagnostics
  explicit rather than hiding them behind a giant SDK wrapper.

## Reusable methods clarified by this wave

- `Engine-native OpenXR extension plugin that injects optional passthrough or composition-layer support without full vendor SDK lock-in`
- `Minimal engine passthrough sample that couples transparent scene configuration with runtime extension calls`
- `Editor-assisted mixed-reality sample that pairs runtime passthrough management with in-app diagnostics`

## Recommended next moves after this wave

1. Treat `ue-openxr-passthrough` as the strongest donor in this wave for
   `clean engine-side extension injection`.
2. Treat `godot_test_passthrough` as the smallest honest donor for a
   `passthrough toggle plus transparent viewport`
   baseline.
3. Keep `mr-openxr-unity-meta-passthrough-sample` visible whenever
   `VR-apps-lab` needs a
   `runtime plus editor setup`
   comparison for Unity.
