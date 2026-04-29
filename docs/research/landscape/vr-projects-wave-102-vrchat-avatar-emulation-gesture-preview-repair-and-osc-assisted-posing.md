# VR Projects Wave 102: VRChat Avatar Emulation, Gesture Preview, Repair, and OSC-Assisted Posing

- Date: `2026-04-30`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat avatar emulation`, `gesture preview`, `repair`, and
  `OSC-assisted posing`.

## Why this wave exists

`VR-apps-lab` needed stronger coverage of
`the creator loop where an avatar is previewed, repaired, emulated, or posed
before final upload or use`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with avatar emulator, gesture preview, fitting-room, and pose
   system queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `lyuma/Av3Emulator` | Strong donor for full avatar emulation with clones, expression menus, and OSC loopback |
| `BlackStartx/VRC-Gesture-Manager` | Strong donor for a radial-menu-based gesture and expression preview harness |
| `JLChnToZ/avautils` | Strong donor for manual avatar repair, fitting-room, and mesh or bone surgery |
| `IlexisTheMadcat/LexisPosingSystem` | Partial but valuable donor for OSC-assisted pose save, history, and scene orchestration |

## Deep-pass notes by project

## `lyuma/Av3Emulator`

- GitHub:
  [lyuma/Av3Emulator](https://github.com/lyuma/Av3Emulator)
- What it is:
  a creator-facing avatar emulator built around PlayableGraph, clone avatars,
  expression menu emulation, and optional OSC integration.
- Why it matters:
  it is the clearest donor in this wave for
  `full avatar rehearsal inside the editor`.
- Interesting ideas:
  create clone avatars for mirror, shadow, or non-local preview; keep an
  expression-menu stack that behaves more like the live avatar; support OSC
  loopback and fake tracking inputs as part of the same preview shell.
- Interesting implementation choices:
  `LyumaAv3Emulator.cs`
  manages runtime lists, clone creation, preview settings, and render hooks;
  `LyumaAv3Menu.cs`
  turns expression-menu navigation into an explicit runtime stack; and
  `LyumaAv3Osc.cs`
  allows OSC send and receive without leaving the preview environment.
- Code donor value:
  very high.
- Product reference value:
  very high.
- Architecture reference value:
  high.
- Caveats:
  it is broad and preview-centric, so future work could still isolate specific
  menu, clone, or OSC branches more deeply.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `full avatar emulator`
  donor.

## `BlackStartx/VRC-Gesture-Manager`

- GitHub:
  [BlackStartx/VRC-Gesture-Manager](https://github.com/BlackStartx/VRC-Gesture-Manager)
- What it is:
  a deep avatar preview harness for testing gestures, expressions, menus, OSC,
  and avatar dynamics directly in Unity.
- Why it matters:
  it is the clearest donor in this wave for
  `gesture and expression preview as a modular tool surface`.
- Interesting ideas:
  keep the preview flow radial-menu driven; bundle debug windows, OSC, tools,
  and culling or tracking dummies into one preview environment; keep edit-mode
  testing available.
- Interesting implementation choices:
  `ModuleVrc3.cs`
  coordinates playable setup, avatar state, debug windows, OSC, tools, and
  dummy avatars; `RadialMenu.cs`
  formalizes preview navigation and puppet surfaces; `OscModule.cs`
  keeps OSC wiring as a first-class debug companion rather than an afterthought.
- Code donor value:
  very high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  it is very broad, so the strongest lessons can disappear if treated as only a
  convenience editor utility.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `preview harness`
  donor.

## `JLChnToZ/avautils`

- GitHub:
  [JLChnToZ/avautils](https://github.com/JLChnToZ/avautils)
- What it is:
  a suite of avatar repair and manipulation tools including mesh combiner, bone
  remapper, fitting-room helpers, and hierarchy utilities.
- Why it matters:
  it is the clearest donor in this wave for
  `manual avatar surgery`
  instead of build-time automation.
- Interesting ideas:
  keep many repair utilities together but still expose narrow windows for each
  job; support remap, combine, cleanup, unwrap, and hierarchy repair without
  assuming one single avatar workflow.
- Interesting implementation choices:
  `MeshCombinerWindow.cs`
  exposes cleanup, merge, blendshape, and lightmap options in a creator-facing
  shell; `BoneRemapper.cs`
  reconstructs hierarchy mappings between source and destination armatures; and
  the core combiner keeps bone remap, submesh merge, and mesh-part removal
  explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is a broad repair suite, so future work could still split out the best
  fitting-room, combiner, or remapper branches for deeper comparison.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `manual avatar repair toolkit`
  donor.

## `IlexisTheMadcat/LexisPosingSystem`

- GitHub:
  [IlexisTheMadcat/LexisPosingSystem](https://github.com/IlexisTheMadcat/LexisPosingSystem)
- What it is:
  a largely paid avatar posing product whose public repo still exposes a rich
  OSC sidecar for save, load, preview, and history orchestration.
- Why it matters:
  it is the clearest partial donor in this wave for
  `external pose companion`
  rather than for a fully open Unity-side posing system.
- Interesting ideas:
  keep pose save, scene save, undo or redo, preset flow, and puppet selection
  in one OSC sidecar; treat the pose helper as a stateful session tool rather
  than a stateless command sender.
- Interesting implementation choices:
  `master_class.py`
  keeps action history, autosave logic, and scene save state explicit;
  `__main__.py`
  manages handshake, version check, and async loop; the public sidecar exposes
  how a pose companion can stay coherent even when the Unity-side asset is not
  fully public.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  the main Unity-side product is not fully public, so this repo must stay
  classified as a partial study instead of a fully exhausted donor.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `OSC pose sidecar`
  donor or access to the public asset surface changes.

## Main takeaways from Wave 102

- `avatar preview and intervention`
  is a coherent branch that deserves its own families and methods.
- The strongest lesson from this wave is that preview, repair, and posing are
  not the same problem:
  `Av3Emulator`
  favors full rehearsal,
  `VRC-Gesture-Manager`
  favors tool-driven preview,
  `avautils`
  favors direct repair, and
  `LexisPosingSystem`
  favors external pose-session orchestration.
- Partially public products can still matter when the visible sidecar or
  session layer exposes a reusable architecture lesson.

## Reusable methods clarified by this wave

- `Clone-based playable avatar emulator with expression-menu stack and OSC loopback`
- `Radial-menu preview harness with avatar-state modules, tracking dummies, and OSC debugging`
- `Avatar repair toolkit with bone remapping, skinned-mesh combine, fitting-room, and hierarchy surgery utilities`
- `OSC sidecar with autosave, undo-history, and puppet-scene pose orchestration`

## Recommended next moves after this wave

1. Keep `Av3Emulator`
   visible as the strongest current
   `full avatar rehearsal`
   donor.
2. Keep `VRC-Gesture-Manager`
   visible as a strong
   `gesture and expression preview harness`
   reference rather than flattening it into generic editor tooling.
3. Compare `Av3Emulator`
   and `VRC-Gesture-Manager`
   whenever future work needs a sharper choice between
   `full emulator`
   and
   `modular preview shell`.
4. Revisit `LexisPosingSystem`
   only if a future pass needs more of the public OSC companion or if the Unity
   side becomes more visible.
