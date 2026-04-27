# VR Projects Wave 99: VRChat World Control Gadgets, Environmental Systems, and Specialized Operator Surfaces

- Date: `2026-04-27`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat world control gadgets`, `environmental systems`, and
  `specialized operator surfaces`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage of creator diagnostics, runtime
substrate, and embodied mechanics than of:

`the small and medium world-control systems that creators actually wire into scenes: depth-buffer fixups, environmental clocks, stage-light operator panels, and keypad access surfaces`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with creator-world control-surface, depth, lighting, and
   keypad queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `Varneon/VUdon-DepthBufferToolkit` | Strong donor for editor-plus-runtime depth-buffer activation in creator worlds |
| `AcChosen/VR-Stage-Lighting` | Strong but broad reference for operator-facing stage-lighting control, DMX grid ingest, and patch export workflows |
| `tommaier123/UdonSharpDayNightController` | Strong donor for a compact synchronized environment controller with local override |
| `MolotovCherry/VRChat_Keypad` | Strong donor for a multi-code keypad surface with object toggles and Udon callback routing |
| `KitKat4191/UdonKeypad` | Strong donor for a compact drag-and-drop keypad with access gating and multi-door routing |

## Deep-pass notes by project

## `Varneon/VUdon-DepthBufferToolkit`

- GitHub:
  [Varneon/VUdon-DepthBufferToolkit](https://github.com/Varneon/VUdon-DepthBufferToolkit)
- What it is:
  a small creator package that helps enable depth rendering on scene cameras
  and mirror cameras in VRChat worlds.
- Why it matters:
  it is the clearest donor in this wave for
  `editor-plus-runtime render fixup`
  rather than for a broad feature package.
- Interesting ideas:
  keep a simple editor menu for scene cameras; add one runtime activator prefab
  for creator convenience; patch mirrors during build rather than requiring
  world authors to hand-wire every mirror camera.
- Interesting implementation choices:
  `Editor/DepthBufferSetupUtility.cs`
  toggles `DepthTextureMode.Depth`
  across scene cameras and can instantiate the activator prefab;
  `DepthBufferActivatorBuildPostProcessor.cs`
  finds the activator, aligns it to the right post-process layer, and adds a
  mirror activator to each configured mirror; `MirrorDepthBufferActivator.cs`
  resolves the generated mirror camera by name on first render and patches its
  depth mode before destroying itself.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is intentionally narrow and tightly tied to VRChat world rendering
  assumptions.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `targeted render-fixup micro-tool`
  donor.

## `AcChosen/VR-Stage-Lighting`

- GitHub:
  [AcChosen/VR-Stage-Lighting](https://github.com/AcChosen/VR-Stage-Lighting)
- What it is:
  a large VRChat lighting package with DMX-driven fixtures, audio-link variants,
  custom render textures, editor tooling, and operator-facing control panels.
- Why it matters:
  it is the clearest broad reference in this wave for
  `world-side operator systems where runtime control, editor setup, and export tooling all matter together`.
- Interesting ideas:
  drive lighting through grid textures and DMX-oriented buffers; keep a local
  control panel for quality and intensity tuning; expose scene patch data
  through export tooling; include a camera configurator for DMX capture layouts.
- Interesting implementation choices:
  `Runtime/Scripts/VRSL_LocalUIControlPanel.cs`
  centralizes runtime quality and intensity controls over materials, toggles,
  render textures, and post effects; `GridReader/GridReader.cs`
  listens for OSC-driven DMX packets and writes them into texture tiles;
  `VRSL_CameraConfigurator.cs`
  constrains DMX camera positioning against target layouts; `Editor/VRSL_DMXPatchExporter.cs`
  and `VRSL_ManagerWindow.cs`
  turn the package into a broader operator and authoring ecosystem rather than
  just a prefab drop.
- Code donor value:
  high.
- Product reference value:
  very high.
- Architecture reference value:
  high.
- Caveats:
  the package is broad enough that a future pass could still split apart
  runtime operators, DMX transport, shader families, and export formats more
  deeply.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `operator-surface and world-control ecosystem`
  reference.

## `tommaier123/UdonSharpDayNightController`

- GitHub:
  [tommaier123/UdonSharpDayNightController](https://github.com/tommaier123/UdonSharpDayNightController)
- What it is:
  a compact synchronized day-night controller for VRChat worlds.
- Why it matters:
  it is the clearest donor in this wave for
  `one shared environmental state with optional local override and several dependent world outputs`.
- Interesting ideas:
  keep the synced state tiny through `SetTime`, `SetSpeed`, and an integer
  change token; allow a local-only mode for preview; drive sun, sky, cloud,
  stars, moon, ambience, audio, and fire effects from one normalized time
  value.
- Interesting implementation choices:
  `CycleController.cs`
  uses one normalized time-of-day value, multiple point-based lerp helpers, and
  a lightweight synced id change to fan one control surface into many world
  outputs without a heavy subsystem split.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is intentionally compact and not a full weather or sky system ecosystem.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `shared environment controller`
  donor.

## `MolotovCherry/VRChat_Keypad`

- GitHub:
  [MolotovCherry/VRChat_Keypad](https://github.com/MolotovCherry/VRChat_Keypad)
- What it is:
  a creator-world keypad prefab with multiple passcodes, object toggles, and
  callback routing into Udon programs.
- Why it matters:
  it is the clearest donor in this wave for
  `keypad as a reusable world-control surface instead of one-off scene logic`.
- Interesting ideas:
  keep input capture, display, settings, and solution validation in separate
  UdonSharp components; allow multiple codes; let each code toggle a different
  object; surface granted or denied or closed callbacks into arbitrary Udon
  programs.
- Interesting implementation choices:
  `Keypad_InputHandler.cs`
  limits and captures input; `Keypad_SolutionChecker.cs`
  handles code matching, object toggles, granted or denied text, and callback
  dispatch; `Keypad_Settings.cs`
  turns codes, object arrays, active-state behavior, and callback programs into
  a declarative setup surface.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  it is more componentized than a tiny prefab and expects creators to wire a
  few cooperating scripts together.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `multi-code routed keypad`
  donor.

## `KitKat4191/UdonKeypad`

- GitHub:
  [KitKat4191/UdonKeypad](https://github.com/KitKat4191/UdonKeypad)
- What it is:
  a compact drag-and-drop keypad prefab with optional allow or deny lists,
  audio cues, callback programs, and additional key or door routing.
- Why it matters:
  it is the clearest donor in this wave for
  `simple keypad integration that still keeps real configuration surface and access gating`.
- Interesting ideas:
  merge primary and secondary codes into a normalized runtime array; support
  allow-list or deny-list overrides; keep one main keypad behaviour plus small
  button scripts; allow optional separation so different codes control
  different doors.
- Interesting implementation choices:
  `Keypad.cs`
  performs configuration validation, merges solution or door arrays, applies
  allow or deny rules, and dispatches callbacks; `KeypadButton.cs`
  keeps button input minimal and supports VR or desktop interaction flow.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is more monolithic than `VRChat_Keypad`, which can make large extensions
  harder even though basic setup is faster.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `compact keypad prefab`
  donor.

## Main takeaways from Wave 99

- `world-control gadget`
  is a broad but coherent creator branch. It spans tiny render fixups, medium
  environmental systems, rich keypad surfaces, and large operator ecosystems.
- The strongest lesson from this wave is that
  `operator surface`
  does not always mean an overlay or external sidecar. It can be a prefab,
  panel, or controller living inside the world.
- Small repos remain worth keeping. `VUdon-DepthBufferToolkit`
  and `UdonSharpDayNightController`
  are both narrow but extremely reusable donors.
- The keypad comparison is especially useful:
  `VRChat_Keypad`
  favors component split and explicit routing, while `UdonKeypad`
  favors compact setup and built-in access gating.

## Reusable methods clarified by this wave

- `Editor-plus-build-postprocess depth-buffer activation for scene cameras and mirrors`
- `Shader-grid and custom-render-texture stage-lighting system with local operator panel and patch export workflow`
- `Shared environment controller with synced global clock and optional local override`
- `Multi-code keypad surface with object toggles and Udon callback routing`
- `Compact drag-and-drop keypad with allow or deny gating and per-code door separation`

## Recommended next moves after this wave

1. Keep `VUdon-DepthBufferToolkit` visible as one of the strongest
   `narrow render-fixup`
   donors in the repo.
2. Keep `VR-Stage-Lighting` visible as a major
   `creator operator ecosystem`
   reference, but treat it as only partially exhausted.
3. Compare `VRChat_Keypad` and `UdonKeypad` whenever future work needs a
   sharper choice between
   `component-split routed keypad`
   and
   `compact all-in-one keypad`.
4. Revisit `UdonSharpDayNightController` whenever `VR-apps-lab` needs a
   smaller
   `shared environment state`
   donor.
