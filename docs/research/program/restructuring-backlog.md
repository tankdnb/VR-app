# Restructuring Backlog

- Date: `2026-04-18`
- Goal: track the work needed to turn `VR.app` into a scalable research base
  and keep the next research phases explicit.

## Status legend

- `Done`
- `In progress`
- `Next`
- `Later`

## Epic A: Documentation topology

### Goal

Move the repository away from a flat `docs/*.md` model and into stable
categories.

### Tasks

- `Done` Create `docs/foundation/`
- `Done` Create `docs/experiments/reality-window/`
- `Done` Create `docs/research/landscape/`
- `Done` Create `docs/research/reuse/`
- `Done` Create `docs/research/program/`
- `Done` Create `docs/research/catalog/`
- `Done` Create `docs/research/templates/`
- `Done` Move existing documents into the new structure
- `Done` Update root navigation in `README.md`
- `Done` Update docs navigation in `docs/README.md`

## Epic B: Research operating model

### Goal

Make repository research repeatable and contributor-friendly.

### Tasks

- `Done` Write a canonical restructuring plan
- `Done` Write a detailed restructuring backlog
- `Done` Write a study method
- `Done` Add a reusable project-study template
- `Done` Add per-folder `README` files for research navigation

## Epic C: Canonical registry and overlap tracking

### Goal

Ensure every tracked repository has a visible place in the system.

### Tasks

- `Done` Keep overlap families in `landscape/project-families.md`
- `Done` Keep priority deep-study backlog in
  `landscape/not-yet-studied-deeply.md`
- `Done` Add `catalog/project-registry.md`
- `Done` Make the registry the canonical entry point for per-project tracking

## Epic D: Comparative matrices

### Goal

Turn large overlap families into side-by-side comparisons instead of more flat
lists.

### Tasks

- `Next` Build `Lighthouse manager matrix`
- `Next` Build `Battery / device monitor matrix`
- `Next` Build `Desktop / overlay UX matrix`
- `Next` Build `Virtual tracker / bridge matrix`
- `Later` Build `Passthrough / reality tools matrix`

## Epic E: High-priority deep-study waves

### Goal

Work through the highest-value partially studied repositories in a disciplined
order.

### Tasks

- `Next` Deep pass on `WebSocket tracker drivers`
  - `John-Dean/OpenVR-Tracker-Websocket-Driver`
  - `surplex-io/OpenVR-Driver`
  - `3NekoSystem/OpenVR-Tracker-Websocket-Driver`
  - `v0xie/OpenVR-Tracker-Websocket-Driver`
- `Next` Deep pass on `VirtualMotionTracker and OSC bridge family`
  - `gpsnmeajp/VirtualMotionTracker`
  - `Greendayle/SteamVR_To_OSC`
  - `ZekkVRC/OpenVR2OSC`
  - `BarakChamo/OpenVR-OSC`
  - `jangxx/steamvr-osc-control`
- `Next` Deep pass on `Vendor enhancement tooling`
  - `BnuuySolutions/PSVR2Toolkit`
  - `MuffinTastic/steamvr-exconfig`
- `Next` Deep pass on `Accessibility overlays`
  - `Vinventive/live-captions-vr`
  - `MochiDoesVR/OpenVRCaptions`
  - notification-assisted overlays
- `Later` Deep pass on `Low-level driver learning path`
  - `terminal29/Simple-OpenVR-Driver-Tutorial`
  - `LucidVR/opengloves-driver`
  - `DaniXmir/GlassVr`
  - `r57zone/OpenVR-ArduinoHMD`
  - `TrueOpenVR/SteamVR-TrueOpenVR`

## Epic F: Quality gates for future additions

### Goal

Stop future research from becoming another unordered pile.

### Tasks

- `Next` Require every new repo addition to update:
  - `catalog/project-registry.md`
  - `landscape/project-families.md` if overlap changed
  - `landscape/not-yet-studied-deeply.md` if follow-up work is needed
- `Next` Require every deep-pass doc to use the standard study template
- `Later` Add scripts or checks to validate internal doc links

## Completion snapshot

The restructuring backlog itself has been carried through to completion for the
in-repo information architecture work.

What remains in the backlog is the `ongoing research program`, not the
restructuring of the repository layout.
