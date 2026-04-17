# Public Roadmap

## Goal

Turn this repository into a practical base for multiple VR utilities while
keeping the original passthrough research documented and reusable.

## Phase 1: Utility Overlay Base

Target:

- stabilize the desktop `OpenVR` utility foundation

Deliverables:

- cleaner overlay interaction model
- wrist dashboard on the right hand
- quick toggles and simple world-space buttons
- persistent settings and profiles
- public-facing docs and repo hygiene

## Phase 2: Reference Windows and Productivity Tools

Target:

- make the overlay foundation useful even without camera passthrough

Deliverables:

- desktop/reference windows in VR
- notes/checklists/timers
- quick launcher panel
- configurable presets for common use cases

## Phase 3: Diagnostics and Power Tools

Target:

- provide utilities that advanced users and VR developers can rely on

Deliverables:

- battery and device status overlays
- tracking/debug info
- input inspection tools
- runtime/overlay metrics
- calibration helpers

## Phase 4: Experimental Reality Tools

Target:

- continue reality-window and passthrough experiments only where support exists

Deliverables:

- external camera provider path
- research-grade projection/cropping/alignment tools
- selected OpenXR passthrough spikes on supported runtimes

## Suggested first products

If the goal is to ship something useful quickly, the strongest order is:

1. `Wrist Dashboard`
2. `Utility Overlay Suite`
3. `Reference Window`
4. `VR Metrics / Device Status Overlay`
5. `Tracking / Calibration Helper`

## Success criteria for the repository

- New tools share one runtime foundation instead of starting from scratch.
- Research findings stay documented and discoverable.
- Public contributors can understand what is production-ready versus
  experimental.
- Each new utility can be built as a focused layer on top of the same base.
