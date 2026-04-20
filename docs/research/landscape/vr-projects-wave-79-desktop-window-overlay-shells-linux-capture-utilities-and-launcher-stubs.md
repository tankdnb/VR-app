# VR Projects Wave 79: Desktop-Window Overlay Shells, Linux Capture Utilities, and Launcher Stubs

- Date: `2026-04-20`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `desktop-window overlay shells`, `Linux capture utilities`, and
  `launcher stubs`.

## Why this wave exists

`VR-apps-lab` already had strong coverage of overlay hosts, dashboard shells,
and Linux desktop-in-VR ecosystems, but it still lacked a cleaner answer to:

`what the smaller, rougher, or older desktop-surface repos teach when they are not polished products`.

This wave exists to make that family clearer:

- legacy Unity shells that bridge desktop capture into overlay textures;
- CLI-first Linux hosts that build capture surfaces through PipeWire and
  portals;
- thin launcher placeholders whose product direction matters more than current
  public source.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with desktop overlay, desktop capture, and launcher queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories studied in this wave

| Project | Why it entered the wave |
|---|---|
| `ShiraoShotaro/DesktopOverlayer` | Useful donor for a Unity desktop-capture overlay with explicit native texture bridge and manual transform controls |
| `nyxpirientity/ovr-penguin` | Strong donor for a CLI-first Linux screen-capture overlay host over PipeWire and OpenVR |
| `gamenew09/RobloxVRLauncher` | Thin launcher placeholder that surfaced as a product-direction node even though the public repo currently has no commits |

## Deep-pass notes by project

## `ShiraoShotaro/DesktopOverlayer`

- GitHub:
  [ShiraoShotaro/DesktopOverlayer](https://github.com/ShiraoShotaro/DesktopOverlayer)
- What it is:
  an older Unity desktop overlay experiment that captures desktop frames through
  a native plugin and projects them into an OpenVR overlay with manual
  transform and alpha controls.
- Why it matters:
  it is the clearest donor in this wave for
  `native desktop capture bridged into a managed overlay surface`.
- Interesting ideas:
  create an external texture from a native grabber; keep overlay transform
  sliders visible in the shell; separate desktop capture from overlay
  registration even in a small prototype.
- Interesting implementation choices:
  `Assets/desktopOVR/DesktopCapture.cs`
  wraps a native `Grabber` plugin and updates an external texture while
  `Assets/desktopOVR/DesktopOverlayer.cs`
  owns OpenVR overlay registration, width, opacity, and absolute transform
  controls.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  older Unity and SteamVR-era assumptions are visible throughout, but the
  explicit texture-bridge pattern is still useful.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `desktop capture to overlay texture`
  reference.

## `nyxpirientity/ovr-penguin`

- GitHub:
  [nyxpirientity/ovr-penguin](https://github.com/nyxpirientity/ovr-penguin)
- What it is:
  a Linux-only CLI tool that creates and controls OpenVR window overlays using
  PipeWire, xdg-desktop-portal, OpenGL, and a small scene graph.
- Why it matters:
  it is the clearest donor in this wave for
  `command-first Linux capture-backed overlay host`.
- Interesting ideas:
  avoid a GUI shell entirely; expose commands, aliases, macro files, and
  serialized executable state; treat screen capture, overlay nodes, and OpenVR
  ownership as separate subsystems under one CLI host.
- Interesting implementation choices:
  `source/main.cpp`
  boots GLFW, PipeWire, and the node tree,
  `source/ovrpenguin.cpp`
  owns the command model and overlay lifecycle, and
  `source/vr/ovr_overlay.cpp`
  handles texture upload, overlay creation, parent selection, transforms, and
  property refresh.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  Linux-only and intentionally rough around the UX edges, but very useful
  because it makes the command and capture boundaries explicit.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `CLI-first overlay host`
  donor.

## `gamenew09/RobloxVRLauncher`

- GitHub:
  [gamenew09/RobloxVRLauncher](https://github.com/gamenew09/RobloxVRLauncher)
- What it is:
  a surfaced launcher-direction node whose public repository currently has no
  commits on `master`.
- Why it matters:
  it is still worth tracking as a reminder that
  `launcher plus desktop helper`
  is a recurring product direction around VR desktop visibility, even when a
  given public repo is not yet a real donor.
- Interesting ideas:
  the idea surface is visible in the repo name and search context, but the
  current public snapshot is effectively a placeholder only.
- Interesting implementation choices:
  none visible yet because the public repo currently contains no committed
  working tree content.
- Code donor value:
  low.
- Product reference value:
  low-medium.
- Architecture reference value:
  low.
- Caveats:
  this is not a current donor repo and should not be overstated.
- What to inspect next:
  treat it as a follow-up watch node only if public source appears later.

## Main takeaways from Wave 79

- `Desktop-window overlay donors` now split more cleanly into:
  - `native texture bridge into managed overlay shell`
  - `CLI-first Linux capture host`
  - `launcher-product placeholder`
- The strongest lesson from this wave is that
  `desktop surface in VR`
  is not only about polished desktop-in-VR platforms. Valuable donor patterns
  also live inside smaller texture-bridge experiments and command-first capture
  shells.
- Another strong lesson is that public placeholder repos should be tracked
  honestly as product-direction nodes, not promoted as donors before the source
  exists.

## Reusable methods clarified by this wave

- `External texture desktop capture bridge that feeds a managed OpenVR overlay surface`
- `CLI-first Linux overlay host that turns portal and PipeWire capture into controllable OpenVR window overlays`

## Recommended next moves after this wave

1. Keep `DesktopOverlayer` visible whenever `VR-apps-lab` needs an older but
   still clear
   `native desktop capture bridge`
   reference.
2. Treat `ovr-penguin` as the strongest donor in this wave for
   `command-first Linux capture overlays`.
3. Keep `RobloxVRLauncher` tracked only as a
   `placeholder watch node`
   until real public source appears.
