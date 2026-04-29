# VR Projects Wave 101: VRChat Avatar Composition, Packaging, and Install Automation

- Date: `2026-04-30`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat avatar composition`, `packaging`, and `install automation`.

## Why this wave exists

`VR-apps-lab` needed clearer coverage of
`the creator workflow after an avatar asset exists but before the project is
actually assembled, installed, and kept healthy`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with avatar composition, package-manager, and install
   automation queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `bdunderscore/modular-avatar` | Strong donor for non-destructive composition, merge-armature processing, and build-time avatar assembly |
| `hai-vr/modular-avatar-as-code` | Strong donor for a code-first facade over composition components |
| `vrc-get/vrc-get` | Strong donor for project-package management, dependency resolution, and GUI plus CLI split |
| `VRLabs/Avatars-3.0-Manager` | Strong donor for multi-tool avatar management, controller merging, and safe asset-copy workflows |

## Deep-pass notes by project

## `bdunderscore/modular-avatar`

- GitHub:
  [bdunderscore/modular-avatar](https://github.com/bdunderscore/modular-avatar)
- What it is:
  a major non-destructive avatar composition system centered on NDMF build
  passes and creator-facing merge components.
- Why it matters:
  it is the clearest donor in this wave for
  `composition as a build pipeline instead of only inspector-time prefab wiring`.
- Interesting ideas:
  treat merge animator, merge armature, and parameter composition as explicit
  build passes; clone menus and assets into saved outputs; retarget meshes and
  prune bones after topology reconciliation.
- Interesting implementation choices:
  `BuildContext.cs`
  wraps NDMF and asset-saving responsibilities into a reusable build context;
  `MergeArmatureHook.cs`
  performs topological armature processing and retention decisions around
  physbones, constraints, and skinned meshes; `MeshRetargeter.cs`
  rewrites bindposes and bone references rather than leaving merge results
  half-manual.
- Code donor value:
  very high.
- Product reference value:
  very high.
- Architecture reference value:
  high.
- Caveats:
  the system is broad enough that future work could still break apart merge
  animator, armature, parameter, and menu branches more deeply.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `non-destructive avatar composition`
  donor.

## `hai-vr/modular-avatar-as-code`

- GitHub:
  [hai-vr/modular-avatar-as-code](https://github.com/hai-vr/modular-avatar-as-code)
- What it is:
  a code-first facade that emits or edits Modular Avatar components from code
  instead of through manual inspector setup.
- Why it matters:
  it is the clearest donor in this wave for
  `code-driven composition over an existing creator component ecosystem`.
- Interesting ideas:
  keep a fluent authoring layer above component generation; allow a dummy mode
  so the same code path can no-op or target alternate roots.
- Interesting implementation choices:
  `MaAc.cs`
  exposes code-first helpers for parameters, menu items, and merge animator
  components; the package keeps authoring intent closer to code while still
  landing inside the established Modular Avatar component model.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is intentionally thin and depends on the broader Modular Avatar ecosystem
  for most runtime meaning.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `code-first facade over Unity creator components`
  donor.

## `vrc-get/vrc-get`

- GitHub:
  [vrc-get/vrc-get](https://github.com/vrc-get/vrc-get)
- What it is:
  a cross-platform VRChat creator project manager with a core library, CLI, and
  GUI.
- Why it matters:
  it is the clearest donor in this wave for
  `package management and project health as first-class creator workflow tooling`.
- Interesting ideas:
  separate environment and package logic into a core library; sync real project
  state into a persistent local database; model dependency resolution across
  locked and unlocked packages and compatibility constraints.
- Interesting implementation choices:
  `project_management.rs`
  normalizes paths and migrates project metadata into a database-backed
  environment store; `resolve.rs`
  handles package compatibility and missing dependency flow; the Tauri GUI
  command layer keeps the desktop shell thin over typed library logic.
- Code donor value:
  very high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  it is less about avatar runtime behavior and more about surrounding creator
  workflow health.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `project package manager`
  donor.

## `VRLabs/Avatars-3.0-Manager`

- GitHub:
  [VRLabs/Avatars-3.0-Manager](https://github.com/VRLabs/Avatars-3.0-Manager)
- What it is:
  an avatar-management shell with editor tabs, helper APIs, and controller or
  menu copying and merge tooling.
- Why it matters:
  it is the clearest donor in this wave for
  `safe multi-tool avatar management over reusable helper APIs`.
- Interesting ideas:
  keep the GUI shell separate from reusable helper functions; discover tabs
  through reflection and attributes; encourage every script-driven output to
  land in its own unique directory.
- Interesting implementation choices:
  `AV3Manager.cs`
  builds a UIElements multi-tab editor shell; `AV3ManagerFunctions.cs`
  exposes reusable creation and copy helpers; `AnimatorCloner.cs`
  and the merger elements formalize controller and parameter-copy behavior
  instead of leaving every tool to reinvent it.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  it sits closer to utility aggregation than to one deep pipeline, so the
  strongest reuse value is in specific helper patterns rather than the whole
  surface at once.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `avatar helper shell`
  donor.

## Main takeaways from Wave 101

- `avatar composition`
  is not just one package or one installer. It spans non-destructive build
  graphs, code-first wrappers, project-package managers, and safe asset-copy
  shells.
- The strongest lesson from this wave is that creators need both
  `composition substrate`
  and
  `project-health tooling`
  to keep large avatar ecosystems manageable.
- `modular-avatar`
  and `vrc-get`
  are especially strong because they show how to keep complex creator workflows
  explicit and inspectable instead of implicit.

## Reusable methods clarified by this wave

- `Code-first facade over avatar composition components with dummy authoring and retargetable root binding`
- `Project-manager split with core resolver library, CLI shell, and GUI background metadata sync`
- `Attribute-discovered multi-tab avatar manager with safe per-run asset output directories`

## Recommended next moves after this wave

1. Keep `modular-avatar`
   visible as the strongest current
   `non-destructive avatar composition`
   donor.
2. Keep `vrc-get`
   visible as one of the strongest
   `creator project manager`
   references in the repo.
3. Compare `modular-avatar-as-code`
   and `Avatars-3.0-Manager`
   whenever future work needs a sharper split between
   `code-first composition facade`
   and
   `GUI-first helper shell`.
4. Revisit `modular-avatar`
   if a later pass needs deeper coverage of merge-order conflicts or advanced
   cross-feature composition.
