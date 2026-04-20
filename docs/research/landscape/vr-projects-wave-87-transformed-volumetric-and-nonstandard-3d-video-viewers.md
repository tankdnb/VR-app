# VR Projects Wave 87: Transformed, Volumetric, and Nonstandard 3D Video Viewers

- Date: `2026-04-20`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `transformed video viewers`, `volumetric or VR180 playback`, and
  `nonstandard 3D media viewing environments`.

## Why this wave exists

`VR-apps-lab` already had ordinary immersive playback coverage, but it still
lacked a cleaner answer to:

`what the strongest donors look like when video is transformed, depth-expanded, volumetric, or embedded in a dome-style viewing environment instead of a simple sphere or screen`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with volumetric video, VR180 playback, depth viewer, and dome
   media tool queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `dfaker/VR-reversal` | Strong donor for a projection-transform media viewer built around `mpv`, `ffmpeg`, and head-motion logging |
| `fbriggs/lifecast_public` | Strong architecture reference for volumetric and VR180 playback spanning WebXR and engine export targets |
| `parkchamchi/DepthViewer` | Strong donor for turning monocular image or video input into a navigable 3D viewer with several inference backends |
| `prefrontalcortex/DomeTools` | Strong product reference for a dome-style viewing environment with local media, `NDI`, and `Spout` ingest |

## Deep-pass notes by project

## `dfaker/VR-reversal`

- GitHub:
  [dfaker/VR-reversal](https://github.com/dfaker/VR-reversal)
- What it is:
  a transformed video viewer that repurposes stereo media and head motion to
  create a different interactive framing workflow over ordinary playback.
- Why it matters:
  it is the clearest donor in this wave for
  `projection-transform media player shell`.
- Interesting ideas:
  let the viewer's head motion influence framing and export decisions; treat
  video reprojection as a reusable playback product, not only as an offline
  edit script; keep ordinary media engines and transform logic loosely coupled.
- Interesting implementation choices:
  `360plugin.lua`
  exposes the transform layer over `mpv` while the surrounding shell leans on
  `ffmpeg` and logging surfaces rather than a bespoke game-engine viewer.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  specialized and somewhat niche, but valuable precisely because it teaches a
  different `player plus transform` product shape.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `nonstandard video reprojection shell`
  donor.

## `fbriggs/lifecast_public`

- GitHub:
  [fbriggs/lifecast_public](https://github.com/fbriggs/lifecast_public)
- What it is:
  a broad volumetric and VR180 playback stack with WebXR player surfaces plus
  export targets for engines such as Unity and Unreal.
- Why it matters:
  it is the clearest architecture reference in this wave for
  `volumetric playback substrate that spans web and engine consumers`.
- Interesting ideas:
  support several media URL and format paths under one viewer family; keep a
  dedicated VR180 mesh path visible; treat volumetric playback as a reusable
  substrate rather than one viewer scene.
- Interesting implementation choices:
  `web/index.html`, `LifecastVideoPlayer11.js`, and `Vr180Mesh.js`
  show how the public player surface, media substrate, and geometry layer fit
  together even though the repo is broad.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broad enough that this remains only
  `Partially studied`
  after the current pass.
- What to inspect next:
  revisit when a future pass needs deeper volumetric, VR180, or export-target
  coverage.

## `parkchamchi/DepthViewer`

- GitHub:
  [parkchamchi/DepthViewer](https://github.com/parkchamchi/DepthViewer)
- What it is:
  a viewer that converts image or video inputs into a depth-expanded 3D surface
  using several inference and transport backends.
- Why it matters:
  it is the clearest donor in this wave for
  `ordinary media expanded into a navigable 3D viewer through depth inference and mesh controls`.
- Interesting ideas:
  treat inference backend choice as part of the public product surface; allow
  media inputs to arrive from files, HTTP, streaming, or remote servers; keep
  the mesh-generation and viewer parameters visible instead of hiding them.
- Interesting implementation choices:
  `MainBehavior.cs`
  and `MeshBehavior.cs`
  show how playback, inference selection, and mesh control sit together as a
  viewing pipeline rather than a simple video player.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  broad and experimental enough that this remains only
  `Partially studied`
  after the current pass.
- What to inspect next:
  revisit if `VR-apps-lab` needs a deeper
  `depth-to-3D viewer`
  donor pass or stronger inference-backend comparisons.

## `prefrontalcortex/DomeTools`

- GitHub:
  [prefrontalcortex/DomeTools](https://github.com/prefrontalcortex/DomeTools)
- What it is:
  a dome-oriented media environment with creator and viewer modes plus local
  media, `NDI`, and `Spout` ingest.
- Why it matters:
  it is the clearest product reference in this wave for
  `immersive media environment with several ingest surfaces and XR menu anchoring`.
- Interesting ideas:
  treat local files, live media feeds, and spatial placement as first-class
  inputs; let the viewer environment itself be the product rather than only one
  player prefab; keep creator and viewer tooling in the same ecosystem.
- Interesting implementation choices:
  `DomeTools.cs`
  plus the viewer-side UI scripts such as `FilesSourceUI.cs`,
  `MediaSourceSelectionContainer.cs`, `VideoController.cs`, and
  `XRMenuAnchor.cs`
  reveal a richer environment and source-ingest shell than a standard
  immersive player.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  broad enough that this remains only
  `Partially studied`
  as a donor.
- What to inspect next:
  revisit when a future pass needs a deeper map of ingest handling, dome-space
  UX, and creator-viewer boundaries.

## Main takeaways from Wave 87

- `Nonstandard 3D playback`
  now splits more cleanly into:
  - `projection-transform player shell over ordinary media engines`
  - `volumetric and VR180 playback substrate`
  - `depth-expanded viewer with inference backends`
  - `immersive dome environment with live and local media ingest`
- The strongest lesson from this wave is that
  `3D video viewer`
  is not one product shape. Some repos derive geometry from depth, some embed
  several ingest modes in an environment, and some transform the viewer's
  perspective over ordinary stereo media.
- Another strong lesson is that many of the most interesting viewers are
  broader than one small donor, so they should be tracked honestly as
  `Partially studied`
  when the first pass only maps the main architecture.

## Reusable methods clarified by this wave

- `Projection-transform media viewer shell over ordinary playback engines with head-motion logging`
- `Volumetric and VR180 playback substrate that spans WebXR and engine export targets`
- `Monocular-depth-to-3D media viewer with pluggable inference backends and mesh controls`
- `Immersive dome-viewer environment with local media, NDI, and Spout ingest`

## Recommended next moves after this wave

1. Treat `VR-reversal` as the strongest
   `transform-driven media player`
   donor in this branch.
2. Keep `lifecast_public` visible as a broader
   `volumetric and VR180 playback substrate`
   that deserves a deeper future pass.
3. Keep `DepthViewer` and `DomeTools` tracked as strong
   `nonstandard 3D viewing environment`
   references rather than ordinary media players.
