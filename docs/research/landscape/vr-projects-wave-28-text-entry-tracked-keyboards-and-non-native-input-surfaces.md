# VR Projects Wave 28: Text Entry, Tracked Keyboards, and Non-Native Input Surfaces

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `text entry`, `tracked keyboards`, and `non-native input surfaces`.

## Why this wave exists

`VR-apps-lab` already had many overlay, diagnostics, and bridge references, but
it still lacked a clearer donor set for one recurring product problem:

- how a VR utility should ask the user to type;
- how much keyboard logic belongs in a toolkit versus a product shell;
- when the right answer is `synthetic keyboard`, `tracked physical keyboard`,
  or `hand-driven typing surface`.

This wave exists to make `text-entry UX in VR` a stronger pattern family inside
`VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with VR keyboard, XR keyboard, tracked keyboard, and
   hand-tracking typing queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `campfireunion/VRKeys` | Strongest focused donor for an evented in-air keyboard prefab with validation and layout switching |
| `ultraleap/XR-Keyboard` | Best reference for a reusable physical keyboard generator with keymaps and runtime spawning |
| `oculus-samples/Unity-TrackedKeyboard` | Strongest tracked physical keyboard sample tied to mixed-reality desk and passthrough UX |
| `Ayfel/MRTK-Keyboard` | Clear donor for a semantic non-native keyboard with multiple layout modes and host callbacks |
| `RTUITLab/Oculus-HandTracking-Keyboard` | Small but useful hand-fingertip typing comparison node |

## Deep-pass notes by project

## `campfireunion/VRKeys`

- GitHub:
  [campfireunion/VRKeys](https://github.com/campfireunion/VRKeys)
- What it is:
  a drum-style VR keyboard for Unity with controller-driven typing,
  layout switching, and host integration events.
- Why it matters:
  it is the clearest donor in the repo for
  `focused synthetic VR keyboard with validation-aware lifecycle`.
- Interesting ideas:
  attach keyboard mallets to hands; allow grab-and-scale placement; expose
  placeholder, validation, and success surfaces; treat submit and cancel as
  first-class keyboard events rather than UI afterthoughts.
- Interesting implementation choices:
  `Assets/VRKeys/Scripts/Keyboard.cs`,
  `Layout.cs`, `LayoutList.cs`, `Placement.cs`, and `DemoScene.cs` make the
  keyboard lifecycle, layout model, and hand-attachment flow easy to inspect.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  optimized around a distinct drum-style interaction model rather than plain
  button tapping.
- What to inspect next:
  compare it directly with `MRTK-Keyboard` to isolate what belongs to a generic
  keyboard contract versus what is specific to one typing interaction style.

## `ultraleap/XR-Keyboard`

- GitHub:
  [ultraleap/XR-Keyboard](https://github.com/ultraleap/XR-Keyboard)
- What it is:
  a reusable physical XR keyboard built around prefabs, keymaps, and a runtime
  manager.
- Why it matters:
  it is the strongest donor in the repo for
  `physical keyboard generator with data-driven keymap configuration`.
- Interesting ideas:
  generate the keyboard from JSON or default keymaps; keep layout data separate
  from the prefab generator; let a manager spawn keyboards relative to target
  input surfaces.
- Interesting implementation choices:
  `KeyboardManager.cs`, `KeyMapGenerator.cs`, `KeyboardSpawner.cs`,
  `JSONKeyMap.cs`, and `DefaultKeyMap.cs` make the manager-versus-generator
  split explicit.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  more of a toolkit slice than a finished end-user product.
- What to inspect next:
  compare its generator-plus-keymap boundary with `VRKeys` to clarify which
  parts of a future `VR-apps-lab` text-entry system should be data-driven.

## `oculus-samples/Unity-TrackedKeyboard`

- GitHub:
  [oculus-samples/Unity-TrackedKeyboard](https://github.com/oculus-samples/Unity-TrackedKeyboard)
- What it is:
  a Quest-focused sample for using a runtime-tracked physical Bluetooth
  keyboard inside MR.
- Why it matters:
  it is the clearest donor in the repo for
  `tracked physical keyboard with hand-proximity reveal and mixed-reality desk context`.
- Interesting ideas:
  bind keyboard visuals to a runtime-tracked desk object; show 2D or 3D
  boundaries; reveal the keyboard only when hands are nearby; connect tracked
  keyboard UX with passthrough and desk awareness instead of treating it as an
  isolated widget.
- Interesting implementation choices:
  `TrackedKeyboardManager.cs`, `KeyboardInteractionManager.cs`,
  `KeyboardVisibility.cs`, and `CustomPointableCanvasModule.cs` make the
  trackable management, visibility heuristics, and temporary canvas-input
  adaptations easy to study.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  tightly tied to Meta runtime features and tracked-keyboard platform support.
- What to inspect next:
  keep it as the main donor whenever a future wave needs stronger
  `desk-aware MR typing` or `tracked hardware keyboard` overlap.

## `Ayfel/MRTK-Keyboard`

- GitHub:
  [Ayfel/MRTK-Keyboard](https://github.com/Ayfel/MRTK-Keyboard)
- What it is:
  a standalone extraction of MRTK's non-native keyboard system.
- Why it matters:
  it is the strongest donor in the repo for
  `semantic spatial keyboard with layout modes and event-driven host integration`.
- Interesting ideas:
  expose `Alpha`, `Symbol`, `URL`, and `Email` keyboard modes; position and
  scale the keyboard relative to the user; provide update, submit, close, and
  navigation events that host apps can consume without owning keyboard internals.
- Interesting implementation choices:
  `NonNativeKeyboard.cs`, `KeyboardKeyFunc.cs`, `KeyboardValueKey.cs`,
  `SymbolKeyboard.cs`, and the prefab structure make the layout-mode and
  callback model explicit.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  it is a keyboard slice extracted from a larger toolkit lineage.
- What to inspect next:
  compare it with `XR-Interaction-Toolkit-Examples` and legacy MRTK hand-menu
  flows to decide what the smallest reusable keyboard contract should be in
  future `VR-apps-lab` utilities.

## `RTUITLab/Oculus-HandTracking-Keyboard`

- GitHub:
  [RTUITLab/Oculus-HandTracking-Keyboard](https://github.com/RTUITLab/Oculus-HandTracking-Keyboard)
- What it is:
  a small hand-tracking keyboard experiment driven by fingertip interaction.
- Why it matters:
  it is a useful comparison donor for the lower-complexity end of the family.
- Interesting ideas:
  use fingertip-triggered key presses; keep keyboard state simple; treat
  caps, shift, and layout switching as a compact local state machine.
- Interesting implementation choices:
  `Assets/Scripts/Keyboard.cs`, `KbKey.cs`, `FingerTip.cs`, and `Display.cs`
  make the minimal `finger -> key -> text` loop very visible.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  much smaller and less generalized than the other donors in this wave.
- What to inspect next:
  use it only as a minimal comparison point when a later prototype wants the
  lightest possible hand-tracking typing surface.

## Main takeaways from Wave 28

- `VR text entry` is not one pattern; the strongest split is:
  - `synthetic evented keyboard`
  - `physical keyboard generator`
  - `tracked hardware keyboard`
  - `semantic non-native keyboard`
  - `minimal fingertip keyboard experiment`
- The best keyboard donors expose more than keys:
  - placement lifecycle
  - layout modes
  - submit/cancel events
  - validation or visibility heuristics
- Tracked physical keyboards matter because they teach `environment-aware UX`,
  not just text input.

## Reusable methods clarified by this wave

- `Tracked physical keyboard with hand-proximity reveal and MR boundary visualization`
- `Non-native spatial keyboard with semantic layouts, validation surfaces, and event callbacks`

## Recommended next moves after this wave

1. Compare `VRKeys`, `XR-Keyboard`, and `MRTK-Keyboard` directly whenever a
   future tool needs a reusable text-entry subsystem.
2. Keep `Unity-TrackedKeyboard` as the main donor for
   `tracked desk keyboard` and `passthrough-adjacent typing` UX.
3. Treat `Oculus-HandTracking-Keyboard` as a small comparison node, not the
   family baseline.
