# VR Projects Wave 42: XR-Glasses Virtual-Display Stacks and Spatial Screen Utilities

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `XR-glasses virtual-display stacks`, `workspace shells`, and
  `spatial screen utilities`.

## Why this wave exists

`VR-apps-lab` already had generic virtual-display references and some glasses
bridges, but a newer special-display branch was still not structured enough:

- base driver stacks that talk to XR glasses directly;
- workspace shells that turn those drivers into a usable desktop experience;
- per-user virtual-display and screen-transformation utilities that serve
  nontraditional displays instead of ordinary VR headsets.

This wave exists to make
`XR-glasses virtual-display stacks and spatial screen utilities`
clearer inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with XR-glasses, virtual-display, spatial-screen, and
   special-display queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `wheaney/XRLinuxDriver` | Strong donor for a base XR-glasses driver stack with device-specific backends and feature hooks |
| `wheaney/breezy-desktop` | Strong donor for a workspace shell layered over the glasses driver, with desktop-environment and Vulkan-mode branches |
| `wheaney/decky-XRGaming` | Focused donor for a SteamOS and Game Mode wrapper around the XR-glasses stack |
| `MolotovCherry/virtual-display-rs` | Strong donor for a user-session virtual-display stack with named-pipe IPC and service boundaries |
| `mgschwan/viture_virtual_display` | Strong donor for turning captured desktop content into a head-tracked screen for Viture hardware |
| `lc700x/desktop2stereo` | Product-rich comparison node for transforming ordinary desktop or video content into a stereoscopic screen workflow |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `peacepenguin/Virtual-Display-Driver` | Already tracked and still valuable, but the stronger new lesson in this wave came from glasses-oriented stacks and cleaner user-session service boundaries |

## Deep-pass notes by project

## `wheaney/XRLinuxDriver`

- GitHub:
  [wheaney/XRLinuxDriver](https://github.com/wheaney/XRLinuxDriver)
- What it is:
  a Linux base driver for XR glasses with device-specific backends and
  feature-level hooks.
- Why it matters:
  it is the clearest donor in the repo for
  `base XR-glasses driver with pluggable features and device backends`.
- Interesting ideas:
  keep raw hardware support separate from higher-level workspace UX; allow
  multiple device families; expose features that other tools can build on.
- Interesting implementation choices:
  `driver.h`,
  `plugins.h`, and
  `features/breezy_desktop.h`
  make the split between `base device driver`, `feature hooks`, and
  `higher-level consumers` explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  Linux-first scope narrows immediate portability, but the decomposition is
  unusually valuable.
- What to inspect next:
  keep it visible whenever a future branch needs
  `special-display hardware access separated from UX shell logic`.

## `wheaney/breezy-desktop`

- GitHub:
  [wheaney/breezy-desktop](https://github.com/wheaney/breezy-desktop)
- What it is:
  a broader workspace shell that sits on top of the XR-glasses driver and
  supports desktop-environment integration plus a separate Vulkan gaming mode.
- Why it matters:
  it is the clearest donor in the repo for
  `workspace shell layered over a special-display driver`.
- Interesting ideas:
  keep workspace UX separate from the base driver; support multiple host
  environments; treat gaming and productivity modes as adjacent but distinct
  branches.
- Interesting implementation choices:
  the repo split between `ui/` and `vulkan/`
  makes the `desktop shell -> environment integration -> game-mode rendering`
  distinction explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  broad scope makes it more honest to keep it as `Partially studied` until a
  future pass digs deeper into all environment-specific branches.
- What to inspect next:
  revisit only when a future branch needs a stronger comparison of
  `driver-backed workspace shell` patterns on Linux.

## `wheaney/decky-XRGaming`

- GitHub:
  [wheaney/decky-XRGaming](https://github.com/wheaney/decky-XRGaming)
- What it is:
  a Decky plugin that wraps installation, configuration, and control for the
  XR-glasses gaming stack in SteamOS Game Mode.
- Why it matters:
  it is the clearest donor in the repo for
  `game-mode control shell around a larger XR display platform`.
- Interesting ideas:
  wrap a lower-level stack with a platform-native control surface; verify
  versions and install state; expose only the high-value toggles to the user.
- Interesting implementation choices:
  `main.py`
  makes the `SteamOS plugin -> install or verify stack -> apply config ->
  control runtime behavior` path explicit.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  most valuable as a wrapper pattern, not as the core display or rendering
  donor itself.
- What to inspect next:
  keep it visible whenever a future branch needs a
  `platform-native wrapper over a heavier XR stack`.

## `MolotovCherry/virtual-display-rs`

- GitHub:
  [MolotovCherry/virtual-display-rs](https://github.com/MolotovCherry/virtual-display-rs)
- What it is:
  a Rust virtual-display stack split into driver, user-session service, CLI,
  bindings, and named-pipe IPC layers.
- Why it matters:
  it is the clearest donor in the repo for
  `per-user virtual display driver coordinated through IPC and user-session services`.
- Interesting ideas:
  keep kernel or driver concerns separate from user-session control; expose a
  structured IPC surface; provide both service and developer-facing control
  layers.
- Interesting implementation choices:
  `ipc.rs` and
  `service.rs`
  make the `driver -> named-pipe IPC -> user-session service -> control app`
  split explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  Windows virtual-display constraints remain, but the service decomposition is
  strong enough to generalize.
- What to inspect next:
  use it whenever a future branch needs `virtual display as a managed service`,
  not only as a driver install.

## `mgschwan/viture_virtual_display`

- GitHub:
  [mgschwan/viture_virtual_display](https://github.com/mgschwan/viture_virtual_display)
- What it is:
  a utility that turns captured desktop content into a head-tracked screen for
  Viture glasses using the device IMU.
- Why it matters:
  it is one of the clearest donors for
  `capture input transformed into a head-tracked virtual screen`.
- Interesting ideas:
  rely on Wayland or screencast capture rather than a full custom runtime;
  pair capture with IMU-based screen stabilization; target a specific hardware
  reality instead of a generic VR product story.
- Interesting implementation choices:
  `v4l2_gl.c`
  shows the `capture or screencast -> GL path -> head-tracked output surface`
  flow in a compact way.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  hardware-specific focus narrows direct reuse, but the screen-utility idea is
  strong.
- What to inspect next:
  keep it visible whenever a future branch needs
  `head-tracked screen utility` rather than a full XR workspace shell.

## `lc700x/desktop2stereo`

- GitHub:
  [lc700x/desktop2stereo](https://github.com/lc700x/desktop2stereo)
- What it is:
  a broad pipeline that uses AI depth estimation to turn desktop or video
  output into a stereoscopic display workflow.
- Why it matters:
  it is a product-rich comparison node for
  `screen transformation rather than ordinary XR rendering`.
- Interesting ideas:
  apply depth estimation as a post-process utility; treat ordinary desktop
  media as convertible screen content; support nontraditional display targets.
- Interesting implementation choices:
  `main.py`
  makes the `capture content -> estimate depth -> produce stereo output`
  utility flow explicit even without deeper runtime integration.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  broad pipeline scope and model assumptions make it more honest to keep as
  `Partially studied`.
- What to inspect next:
  revisit only if a future branch needs a narrower comparison of
  `AI screen transformation` versus more direct display-driver approaches.

## Main takeaways from Wave 42

- `XR-glasses workflows` are now a distinct family, not just a footnote inside
  generic virtual displays.
- The strongest split in this family is:
  - `base hardware driver`
  - `workspace shell`
  - `game-mode wrapper`
  - `user-session virtual display service stack`
  - `capture-to-head-tracked screen utility`
  - `screen transformation pipeline`
- The most reusable lesson is that `special displays` benefit from a layered
  stack:
  - keep hardware access separate from workspace UX
  - keep user-session display control separate from driver install
  - keep screen transformation or capture tools honest about their target
    display assumptions

## Reusable methods clarified by this wave

- `XR-glasses platform split across base driver, workspace shell, and game-mode wrapper`
- `User-session virtual display service coordinated through named-pipe IPC`
- `Captured desktop or video content transformed into a head-tracked spatial screen`

## Recommended next moves after this wave

1. Treat `XRLinuxDriver` as the main low-level donor whenever a future branch
   needs `special-display hardware access`.
2. Keep `breezy-desktop` visible as the main product reference for
   `workspace shell over XR glasses`, while honestly leaving it as
   `Partially studied`.
3. Use `virtual-display-rs` whenever a future branch needs a
   `managed virtual display service stack` on Windows.
4. Keep `viture_virtual_display` and `desktop2stereo` together as comparison
   nodes for `screen utility` ideas that are not full workspace shells.
