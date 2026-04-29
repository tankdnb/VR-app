# VR Projects Wave 100: VRChat Avatar Setup, Optimization, and Quest Portability

- Date: `2026-04-30`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat avatar setup`, `optimization`, and `Quest portability`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage of world-authoring helpers than of
`the avatar pipeline that creators actually use before upload: setup
workbenches, Quest conversion passes, upload-time optimizers, and DCC-side
scalers`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with avatar setup, Quest conversion, optimizer, and scaler
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `rurre/PumkinsAvatarTools` | Strong donor for an editor workbench that unifies avatar copying, pose editing, thumbnails, and project-scoped setup state |
| `kurotu/VRCQuestTools` | Strong donor for non-destructive Quest conversion and validator automation across the avatar build pipeline |
| `d4rkc0d3r/d4rkAvatarOptimizer` | Strong donor for deep upload-time optimization that spans meshes, materials, shaders, and animator graphs |
| `triazo/immersive_scaler` | Strong donor for DCC-side avatar scaling and body-proportion alignment before Unity import |

## Deep-pass notes by project

## `rurre/PumkinsAvatarTools`

- GitHub:
  [rurre/PumkinsAvatarTools](https://github.com/rurre/PumkinsAvatarTools)
- What it is:
  a broad Unity editor workbench for VRChat avatar setup, migration, posing,
  thumbnail creation, and utility operations.
- Why it matters:
  it is the clearest donor in this wave for
  `avatar setup as one reusable editor shell instead of a pile of one-off menu commands`.
- Interesting ideas:
  keep one large avatar workbench window; split persistent configuration into a
  project-scoped pref layer; bundle copier helpers, pose editing, and texture
  or thumbnail support inside the same operator-facing tool.
- Interesting implementation choices:
  `PrefManager.cs`
  scopes editor keys under a product-name prefix so settings survive cleanly
  across projects; `PumkinsPoseEditor.cs`
  builds a dedicated pose-authoring window with persistent selection and scene
  hooks; `CopyInstance.cs`
  and the copier infrastructure keep from or to object mapping, ignored
  transforms, and copy-state bookkeeping explicit instead of ad hoc.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is broad and editor-heavy, so some sub-tools would still benefit from a
  future pass that isolates the strongest copier or pose-specific layers.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `avatar workbench`
  or
  `project-scoped editor state`
  donor.

## `kurotu/VRCQuestTools`

- GitHub:
  [kurotu/VRCQuestTools](https://github.com/kurotu/VRCQuestTools)
- What it is:
  a package-centered avatar conversion and validation toolchain for making
  VRChat avatars portable to Quest or Android targets.
- Why it matters:
  it is the clearest donor in this wave for
  `non-destructive mobile conversion with validator and setup automation`.
- Interesting ideas:
  keep Quest conversion as a repeatable pipeline instead of a one-shot manual
  rewrite; validate avatars automatically while creators edit; track asset
  replacements explicitly so material, animation clip, and controller swaps do
  not become invisible.
- Interesting implementation choices:
  `ValidationAutomator.cs`
  hooks hierarchy and edit-mode changes to revalidate loaded avatars;
  `AvatarConverterPassUtility.cs`
  keeps NDMF phase handling and replaced-object registration explicit; the
  package also exposes guided setup through
  `AvatarConverterWindow.cs`
  and detailed material warnings through
  `MaterialConversionGUI.cs`.
- Code donor value:
  very high.
- Product reference value:
  very high.
- Architecture reference value:
  high.
- Caveats:
  it depends heavily on the VRChat avatar ecosystem and NDMF-specific build
  integration, so some patterns are ecosystem-bound rather than general Unity
  editor patterns.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `validator-driven conversion pipeline`
  donor.

## `d4rkc0d3r/d4rkAvatarOptimizer`

- GitHub:
  [d4rkc0d3r/d4rkAvatarOptimizer](https://github.com/d4rkc0d3r/d4rkAvatarOptimizer)
- What it is:
  a build-hook avatar optimizer that rewrites and strips avatar content before
  upload.
- Why it matters:
  it is the clearest donor in this wave for
  `optimization as a staged graph-aware and shader-aware pipeline`
  rather than a simple mesh merge.
- Interesting ideas:
  inject a default optimizer component on upload when needed; treat shader
  analysis as a gate before material merging; optimize animator controllers as
  aggressively as meshes and materials.
- Interesting implementation choices:
  `AvatarBuildHook.cs`
  explicitly orders itself around other avatar build tooling and can auto-add a
  default optimizer component; `d4rkAvatarOptimizer.cs`
  runs a long staged optimization pass from unused component stripping through
  animator fixes; `ShaderAnalyzer.cs`
  parses shader structure to decide what can be merged and why not; and
  `AnimatorOptimizer.cs`
  rewrites layers, controllers, and blend trees instead of leaving animation
  cost untouched.
- Code donor value:
  very high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the tool is dense and some of its strongest value sits in optimization
  heuristics that would still benefit from future comparative study.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `upload-time optimization pipeline`
  donor.

## `triazo/immersive_scaler`

- GitHub:
  [triazo/immersive_scaler](https://github.com/triazo/immersive_scaler)
- What it is:
  a Blender add-on for avatar scaling and alignment around VRChat-relevant body
  proportions.
- Why it matters:
  it is the clearest donor in this wave for
  `DCC-side preprocessing before Unity import`
  instead of only Unity-side fixes.
- Interesting ideas:
  compute avatar metrics from real mesh geometry rather than only bone lengths;
  keep user-facing controls for height, upper-body ratio, limb thickness, and
  eye scaling; align source and target armatures proportionally instead of
  only applying one scalar.
- Interesting implementation choices:
  `operations.py`
  extracts lowest or highest points, eye height, hand reach, and other body
  metrics using world-space mesh data; `align.py`
  performs torso and limb alignment with head and shoulder compensation; the UI
  surface exposes avatar-specific scale semantics rather than generic Blender
  transforms.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is Blender-side tooling, so the strongest reuse value is in algorithmic
  ideas and DCC workflow structure rather than direct Unity integration.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `body-metric scaler`
  donor or a bridge between DCC preprocessing and Unity avatar setup.

## Main takeaways from Wave 100

- `avatar setup`
  is a coherent engineering branch, not just miscellaneous creator clutter.
- The strongest lesson from this wave is that creators rely on several
  different layers together:
  editor workbenches, validator-driven converters, upload-time optimizers, and
  DCC-side preprocessors.
- Small or narrow utilities still matter, but the biggest donor value here
  comes from tools that keep their own pipeline state visible.
- `VRCQuestTools`
  and `d4rkAvatarOptimizer`
  are especially strong because they expose how to treat build-time avatar
  mutation as an explicit system rather than an opaque black box.

## Reusable methods clarified by this wave

- `Editor workbench with project-scoped Unity prefs and dedicated pose editing for avatar setup`
- `Generic avatar copier pipeline with ignored-transform mapping and migration-oriented copy bookkeeping`
- `Non-destructive avatar converter that injects validator automators and tracks asset replacements through NDMF passes`
- `Upload-triggered avatar optimizer with shader-merge analysis and animator-controller rewrite stages`

## Recommended next moves after this wave

1. Keep `PumkinsAvatarTools`
   visible as a strong
   `avatar workbench`
   reference rather than treating it as a random legacy utility bundle.
2. Keep `VRCQuestTools`
   visible as one of the strongest current
   `Quest portability`
   donors in the repository.
3. Compare `d4rkAvatarOptimizer`
   against other optimizers whenever future work needs a sharper split between
   `mesh cleanup`
   and
   `full avatar graph optimization`.
4. Revisit `immersive_scaler`
   whenever `VR-apps-lab` needs a better bridge from DCC-side proportional
   cleanup into creator upload workflows.
