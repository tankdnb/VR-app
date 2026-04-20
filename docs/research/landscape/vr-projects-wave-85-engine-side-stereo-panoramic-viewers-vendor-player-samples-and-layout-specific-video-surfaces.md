# VR Projects Wave 85: Engine-Side Stereo Panoramic Viewers, Vendor Player Samples, and Layout-Specific Video Surfaces

- Date: `2026-04-20`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `engine-side stereo panoramic viewers`, `vendor player samples`, and
  `layout-specific video surfaces`.

## Why this wave exists

`VR-apps-lab` already had broader immersive media coverage, but it still
lacked a cleaner answer to:

`what the most reusable engine-side immersive video patterns look like when playback is represented as scene components, layout enums, or vendor sample matrices`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with Unity panoramic player, Unreal stereo panoramic player,
   and vendor XR video sample queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `ft-lab/Unity_Panorama180View` | Strong donor for a compact Unity component that unifies image and video playback across several projection modes |
| `picoxr/VideoPlayer-UnityXR` | Strong vendor reference for layout-specific playback scenes and materials across 360, stereo, and cubemap-style paths |
| `UNAmedia/ue5-stereo-panoramic-player-demo` | Useful product reference for an Unreal panoramic player split between high-level authoring tools and lower-level programmable surfaces |

## Deep-pass notes by project

## `ft-lab/Unity_Panorama180View`

- GitHub:
  [ft-lab/Unity_Panorama180View](https://github.com/ft-lab/Unity_Panorama180View)
- What it is:
  a Unity panoramic viewer package that supports several 180 or 360 image and
  video layouts through one component and shader path.
- Why it matters:
  it is the clearest donor in this wave for
  `single component plus projection enum plus shader-backed sphere rendering`.
- Interesting ideas:
  keep still-image and video playback under one panoramic component; expose
  layout modes directly in code; treat shader selection and texture routing as
  a reusable projection problem rather than as per-scene custom logic.
- Interesting implementation choices:
  `Panorama180View.cs`
  owns playback setup and layout selection while
  `panoramaSphereRendering.shader`
  keeps projection-specific rendering behavior visible; the same package
  handles 360 top-bottom, 180 side-by-side, and fisheye layouts without
  splitting into separate apps.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  compact and clear, but mostly focused on the viewing surface rather than a
  broader operator shell.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `Unity panoramic surface baseline`
  donor.

## `picoxr/VideoPlayer-UnityXR`

- GitHub:
  [picoxr/VideoPlayer-UnityXR](https://github.com/picoxr/VideoPlayer-UnityXR)
- What it is:
  a vendor sample pack for Unity XR playback that demonstrates several layout
  modes such as 360, side-by-side 3D, over-under 3D, and `360_3D`.
- Why it matters:
  it is the clearest reference in this wave for
  `layout-specific sample matrix`
  rather than one generalized player abstraction.
- Interesting ideas:
  make layout modes concrete through scenes, materials, and mesh choices; keep
  different video formats visibly separate so integrators can copy the right
  sample instead of guessing one universal path.
- Interesting implementation choices:
  `playController.cs`
  and `Pvr_Cubemapcube.cs`
  show the playback-control and geometry layers while the sample scenes and
  material setup demonstrate how vendor-facing XR video support often ships as
  a matrix of reference layouts rather than one reusable component.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  strongest as a vendor reference and layout checklist, not as a reusable
  framework.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `vendor sample for playback layout coverage`
  comparison.

## `UNAmedia/ue5-stereo-panoramic-player-demo`

- GitHub:
  [UNAmedia/ue5-stereo-panoramic-player-demo](https://github.com/UNAmedia/ue5-stereo-panoramic-player-demo)
- What it is:
  a public Unreal demo client for a stereo panoramic player plugin where the
  actual plugin is distributed separately.
- Why it matters:
  it is the clearest product reference in this wave for
  `high-level authoring surface paired with lower-level programmable panoramic actor`.
- Interesting ideas:
  separate `Panoramic Director` from `Panoramic Sphere` so quick authoring and
  lower-level control do not collapse into one actor; make cinematic or tour
  assembly feel like a content workflow instead of a raw rendering demo.
- Interesting implementation choices:
  the public repo mainly exposes the demo application's configuration and scene
  structure, which still makes the product split visible even though the core
  plugin code is external.
- Code donor value:
  low-medium.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  the main playback plugin is not included, so this remains only
  `Partially studied`
  as a donor.
- What to inspect next:
  revisit only when a future pass needs a closer map of the actual plugin
  boundary rather than the public demo shell.

## Main takeaways from Wave 85

- `Engine-side immersive playback`
  now splits more cleanly into:
  - `single-component panoramic sphere with layout enum and shader path`
  - `vendor layout matrix expressed as sample scenes and materials`
  - `high-level panoramic authoring tools over a lower-level viewing actor`
- The strongest lesson from this wave is that
  `engine-side video playback`
  is often more reusable when layout, scene shape, or authoring level is made
  explicit instead of buried in one generic prefab.
- Another strong lesson is that
  `demo repos without their core plugin`
  still matter as product and architecture references when they expose a strong
  authoring split honestly.

## Reusable methods clarified by this wave

- `Unity panoramic sphere component with image and video parity plus shader-backed projection modes`
- `Vendor sample matrix for 360, stereo side-by-side, over-under, and related layout-specific playback surfaces`
- `High-level panoramic tour actor paired with lower-level programmable panoramic sphere`

## Recommended next moves after this wave

1. Keep `Unity_Panorama180View` visible as a compact, high-signal
   `projection surface donor`.
2. Treat `VideoPlayer-UnityXR` as a useful
   `layout coverage reference`
   rather than expecting one generalized playback framework from it.
3. Keep `ue5-stereo-panoramic-player-demo` tracked honestly as a
   `product and authoring split`
   reference until the underlying plugin surface is better exposed.
