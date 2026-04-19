# VR Projects Wave 58: Micro-Overlays, Timed Status Surfaces, and Plugin-Fed Informational Display Helpers

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `micro-overlays`, `timed status surfaces`, and
  `plugin-fed informational display helpers`.

## Why this wave exists

`VR-apps-lab` already had broader overlay hosts and contextual display
surfaces, but another smaller and more product-shaped branch still needed a
cleaner donor map:

- tiny overlays driven by a local `HTTP` or `OSC` control plane;
- informational surfaces that pull data from plugins or provider scripts;
- timer overlays that transition from passive HUD to harder interruption;
- rough note-style overlays that reveal the minimum state model needed for
  overlay-native writing or annotation.

This wave exists to make
`micro-overlays, timed status surfaces, and plugin-fed informational display helpers`
clearer inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with micro-overlay, timer-overlay, notebook-overlay, and
   local API-driven overlay queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `R-VUt/OVRBrightnessAPI` | Strong donor for a tiny overlay controlled by local `HTTP` or `OSC`, with one very focused user value |
| `CorvinRyder/VR-Slideshow-Overlay` | Strong donor for an informational surface driven by plugins and multiple output sinks |
| `Podshot/VRSessionTimer` | Strong donor for a timer overlay that escalates into notifications and restart flows |
| `Yukiiro-Nite/notebook-vr-overlay` | Useful lower-bound donor for a rough note-surface overlay with explicit event plumbing and future writing hooks |

## Deep-pass notes by project

## `R-VUt/OVRBrightnessAPI`

- GitHub:
  [R-VUt/OVRBrightnessAPI](https://github.com/R-VUt/OVRBrightnessAPI)
- What it is:
  a very small overlay that attaches a black quad to the HMD and adjusts its
  opacity through either a local `HTTP` or `OSC` interface.
- Why it matters:
  it is the clearest donor in the repo for
  `tiny overlay plus tiny local control plane`.
- Interesting ideas:
  treat brightness as a post-process-like comfort layer without modifying the
  main VR app; keep the control surface tiny enough to be automated from
  external tools; provide both `HTTP` and `OSC` variants for the same core
  overlay value.
- Interesting implementation choices:
  `OVRBrightnessAPI/Program.cs`
  and `OSCBrightness/Program.cs`
  make the
  `overlay lifecycle -> local control endpoint -> alpha update`
  path explicit in two different transport variants.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  intentionally tiny and narrow, but that narrowness is the whole product
  lesson.
- What to inspect next:
  keep it visible whenever a future branch needs
  `micro-overlay with an automation-friendly local API`.

## `CorvinRyder/VR-Slideshow-Overlay`

- GitHub:
  [CorvinRyder/VR-Slideshow-Overlay](https://github.com/CorvinRyder/VR-Slideshow-Overlay)
- What it is:
  a Python-based informational surface that can display slideshow-like data in
  VR, with plugins providing data and multiple output sinks including an overlay
  renderer, `VRChat` chatbox, and file output.
- Why it matters:
  it is the clearest donor in the repo for
  `plugin-fed informational surface with multiple output channels`.
- Interesting ideas:
  separate information providers from presentation sinks; let the same data
  feed an in-headset overlay, an avatar-facing chatbox, or a file; use a
  lightweight desktop shell to manage plugins and output selection.
- Interesting implementation choices:
  `src/plugins/ForegroundWindow.py`
  demonstrates the provider model,
  `src/output_ports/VROverlay.py`
  isolates the overlay sink, and
  `src/vr_overlay.py`
  shows the overlay-side rendering boundary.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the UI shell is rough, but the `providers plus output ports` split is a very
  reusable donor pattern.
- What to inspect next:
  keep it visible whenever a future branch needs
  `overlay as one sink among several consumer channels`.

## `Podshot/VRSessionTimer`

- GitHub:
  [Podshot/VRSessionTimer](https://github.com/Podshot/VRSessionTimer)
- What it is:
  a `Qt` timer utility that renders session time in an overlay and escalates to
  `OpenVR` notifications with close or restart flows.
- Why it matters:
  it is the clearest donor in the repo for
  `timer overlay that escalates from passive HUD to active reminder loop`.
- Interesting ideas:
  keep the timer readable as a passive overlay most of the time; move to a
  stronger notification only when thresholds are crossed; let the loop support
  dismissal or restart instead of a one-shot reminder only.
- Interesting implementation choices:
  `mainwindow.cpp`
  owns the timer state,
  `overlaywidget.cpp`
  holds the overlay UI, and
  `vrnotification.cpp`
  plus `openvroverlaycontroller.cpp`
  make the escalation path explicit.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  narrow domain, but very clear product framing and escalation behavior.
- What to inspect next:
  keep it visible whenever a future branch needs
  `timed reminder overlay with stronger intervention states`.

## `Yukiiro-Nite/notebook-vr-overlay`

- GitHub:
  [Yukiiro-Nite/notebook-vr-overlay](https://github.com/Yukiiro-Nite/notebook-vr-overlay)
- What it is:
  a rough C++ prototype that loads an image file into an overlay and begins to
  wire overlay mouse events toward a future notebook or writing workflow.
- Why it matters:
  it is a useful lower-bound donor for
  `note surface with explicit event plumbing`, even though the product is not
  finished.
- Interesting ideas:
  start with a persistent image surface; treat overlay mouse events as the base
  of future note interaction; leave save or drawing work as explicit next-step
  hooks instead of hiding the incompleteness.
- Interesting implementation choices:
  `src/notebook-vr-overlay.cpp`
  makes the
  `image load -> overlay create -> event polling -> future writing hooks`
  path visible in one place.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  clearly incomplete, so it should stay a `Partially studied` lower-bound node
  rather than an over-promoted product donor.
- What to inspect next:
  revisit only if a future branch needs deeper note persistence, drawing, or
  `overlay-native writing` comparisons.

## Main takeaways from Wave 58

- `Micro-overlays` are clearer when split into:
  - `tiny local control-plane overlays`
  - `provider-fed informational surfaces`
  - `timer overlays with escalation loops`
  - `rough note-surface lower-bound prototypes`
- The strongest lesson from this wave is that a small overlay becomes much more
  reusable once its control plane or provider model is explicit.
- Another strong lesson is that `informational surface` and `notification
  surface` are different product modes, even when both use the same overlay
  APIs.

## Reusable methods clarified by this wave

- `Micro-overlay exposed as a tiny local HTTP or OSC control plane`
- `Plugin-fed informational surface with reusable providers and multiple output sinks`
- `Timer-driven overlay that escalates from passive HUD to closeable notification and restart loop`

## Recommended next moves after this wave

1. Treat `OVRBrightnessAPI` as the smallest possible donor for
   `micro-overlay plus local automation surface`.
2. Keep `VR-Slideshow-Overlay` visible whenever `VR-apps-lab` needs a
   `provider-fed informational overlay` instead of another monolithic HUD.
3. Keep `VRSessionTimer` visible whenever a future branch needs
   `timer plus escalation` behavior.
4. Keep `notebook-vr-overlay` as an honest lower-bound note-surface reference,
   not as a mature benchmark.
