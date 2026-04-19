# VR Projects Wave 57: Linux Overlay Control Shells, Desktop-Service Panels, and Interaction Variants

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `Linux overlay control shells`, `desktop-service panels`, and
  `interaction variants`.

## Why this wave exists

`VR-apps-lab` already had several overlay hosts and dashboard utilities, but
the Linux-oriented branch still needed a cleaner donor map:

- overlays that behave like desktop-control shells instead of generic display
  mirrors;
- control panels that wrap desktop services such as audio routing, media, or
  session helpers;
- interaction variants where controller rays, on-overlay keyboard helpers, and
  desktop debug modes matter as much as the visible panel;
- Linux-first repos whose value comes from operating-model differences, not
  just from being another overlay app.

This wave exists to make
`Linux overlay control shells, desktop-service panels, and interaction variants`
clearer inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with Linux overlay, `X11`, Qt panel, and desktop-service
   overlay queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `galister/OVR4X11` | Strong donor for a Linux overlay shell that mixes `X11` screen capture, controller-pointer interaction, and an on-overlay keyboard |
| `DrogonMar/SVRLinuxTools` | Strong donor for a Linux desktop-service panel host with `Qt`, multiple control surfaces, and a useful `--novr` debug path |
| `Dragon092/OpenVR_Audio_Manager` | Strong donor for an audio-routing overlay with device enumeration and HMD-aware preference logic |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `CrispyPin/sinpin-vr` | GitHub now acts mostly as a relocation stub to Codeberg, so the public donor surface on GitHub is too thin for a mainline deep-pass promotion |

## Deep-pass notes by project

## `galister/OVR4X11`

- GitHub:
  [galister/OVR4X11](https://github.com/galister/OVR4X11)
- What it is:
  a Unity-based Linux overlay shell for interacting with ordinary `X11`
  windows in SteamVR.
- Why it matters:
  it is one of the clearest donors in the repo for
  `desktop screen-control overlay with controller-mouse adaptation`.
- Interesting ideas:
  treat controller orientation as a modifier for screen pointer movement;
  support on-overlay keyboard entry instead of forcing desktop fallback; make
  show or hide behavior part of the workflow instead of assuming the overlay is
  always present.
- Interesting implementation choices:
  `Overlay/OverlayManager.cs`
  and `X11Screen/ScreenOverlay.cs`
  make the
  `captured screen -> overlay surface -> controller interaction`
  path explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  Linux, Unity, and `X11` assumptions narrow the portability, but the
  interaction pattern is still very reusable.
- What to inspect next:
  keep it visible whenever a future branch needs
  `desktop control in VR without a full browser stack`.

## `DrogonMar/SVRLinuxTools`

- GitHub:
  [DrogonMar/SVRLinuxTools](https://github.com/DrogonMar/SVRLinuxTools)
- What it is:
  a `Qt` or KDE-style Linux overlay toolkit that gathers several desktop
  control surfaces under one SteamVR-facing shell and also supports a
  `--novr` debug path.
- Why it matters:
  it is the clearest donor in the repo for
  `desktop-service overlay shell with a non-VR debug mode`.
- Interesting ideas:
  treat the overlay as a panel host rather than one fixed app; preserve a
  desktop-only execution path for debugging and iteration; keep Linux service
  control inside the same shell as media and audio helpers.
- Interesting implementation choices:
  `src/main.cpp`
  exposes the `--novr` pathway, while
  `src/MainOverlay/MainOverlay.cpp`
  shows how the panel host and service controls are organized.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  broad and a bit rough around the edges, but the `one shell, many service
  panels` lesson is unusually strong.
- What to inspect next:
  keep it visible whenever a future branch needs
  `overlay shell plus desktop-service panel host`.

## `Dragon092/OpenVR_Audio_Manager`

- GitHub:
  [Dragon092/OpenVR_Audio_Manager](https://github.com/Dragon092/OpenVR_Audio_Manager)
- What it is:
  a `Qt` dashboard overlay that switches input and output devices based on VR
  headset presence and user preferences.
- Why it matters:
  it is the clearest donor in the repo for
  `device-manager overlay with HMD-aware routing state`.
- Interesting ideas:
  treat audio routing as a user-facing overlay problem instead of a hidden
  startup script; persist preferred devices for `VR on` and `VR off` states;
  keep enumeration, preferences, and overlay scene split into clean units.
- Interesting implementation choices:
  `audiostatecontroller.cpp`
  captures the preference and routing model,
  `openvroverlaycontroller.cpp`
  handles the overlay surface, and
  `overlaywidget.cpp`
  makes the panel UI boundary explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  a narrow domain-specific tool, but that narrowness is exactly what makes the
  donor lesson concrete.
- What to inspect next:
  keep it visible whenever a future branch needs
  `device inventory or routing overlay with persisted preferences`.

## Main takeaways from Wave 57

- `Linux overlay control shells` are clearer when split into:
  - `screen-control overlay with controller-mouse interaction`
  - `desktop-service panel host`
  - `device-manager dashboard with HMD-aware routing logic`
- A strong Linux-side lesson is that `non-VR debug mode` is not just a
  convenience. It is a real maintainability pattern for overlay shells.
- Another strong lesson is that controller interaction design matters as much as
  the actual service being controlled.

## Reusable methods clarified by this wave

- `Linux desktop or system-service overlay shell with a non-VR debug path and controller-mouse interaction`

## Recommended next moves after this wave

1. Keep `OVR4X11` visible whenever `VR-apps-lab` needs Linux-side
   `desktop interaction in VR`.
2. Treat `SVRLinuxTools` as the main donor for `panel host plus non-VR debug
   path`.
3. Treat `OpenVR_Audio_Manager` as a focused product reference for
   `stateful routing overlay` design.
