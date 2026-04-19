# VR Projects Wave 59: Embodied Locomotion Overlays, Live Tuning Surfaces, and External-Device Control Panels

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `embodied locomotion overlays`, `live tuning surfaces`, and
  `external-device control panels`.

## Why this wave exists

`VR-apps-lab` already had control overlays, haptics bridges, and simulator
panels, but another adjacent branch still needed a cleaner donor map:

- overlays that directly shape locomotion or bodily control intent;
- desktop editors whose live state appears in VR as a tuning surface;
- overlays that control external hardware through a persisted config and remote
  API model;
- older lineage nodes that help explain how a stronger modern donor emerged.

This wave exists to make
`embodied locomotion overlays, live tuning surfaces, and external-device control panels`
clearer inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with locomotion-overlay, tuning-overlay, and device-panel
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `hiinaspace/bikeheadvr` | Strong donor for a controllerless locomotion overlay that turns foot-tracker motion and gaze interaction into avatar-facing movement intent |
| `MartyDude20/Omni-Tune` | Strong donor for a desktop editor whose state is mirrored into a live VR tuning surface through a native helper |
| `OpenShock/OVR-Shock` | Strong donor for a modern external-device control overlay with persisted config, remote API client, and hand-specific UI |
| `OpenShock/VROverlay` | Useful lineage node for comparing an older Unity-based device-control overlay against the newer `OVR-Shock` implementation |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `NewChromantics/PopExposeXr` | Interesting concept for exposing XR state outward, but the current public repo is too thin to justify mainline promotion in this wave |

## Deep-pass notes by project

## `hiinaspace/bikeheadvr`

- GitHub:
  [hiinaspace/bikeheadvr](https://github.com/hiinaspace/bikeheadvr)
- What it is:
  a Python overlay and control stack that estimates bicycle pedaling from foot
  trackers, uses gaze-driven buttons, and exports motion intent through
  `VRChat` `OSC`.
- Why it matters:
  it is the clearest donor in the repo for
  `embodied locomotion overlay that maps body motion into avatar-control intent`.
- Interesting ideas:
  keep locomotion control controllerless; treat gaze buttons as the minimal VR
  control surface; combine sensor estimation, overlay UI, runtime hookup, and
  avatar-facing output into a tight embodied workflow.
- Interesting implementation choices:
  `src/bikeheadvr/overlay_ui.py`
  exposes the overlay control surface,
  `pedal_estimation.py`
  shows the motion inference layer, and
  `vr_runtime.py`
  plus `vrchat_osc.py`
  make the runtime and output boundaries explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  domain-specific and tied to one locomotion idea, but the `sensor estimate ->
  overlay control -> avatar-facing output` pattern is strong.
- What to inspect next:
  keep it visible whenever a future branch needs
  `controllerless locomotion overlay patterns`.

## `MartyDude20/Omni-Tune`

- GitHub:
  [MartyDude20/Omni-Tune](https://github.com/MartyDude20/Omni-Tune)
- What it is:
  an `Electron` or React desktop profile editor paired with a native VR helper
  that mirrors tuning state into a live overlay surface.
- Why it matters:
  it is the clearest donor in the repo for
  `desktop editor plus native VR helper over a framed streaming protocol`.
- Interesting ideas:
  let the real editing workflow stay on desktop while still exposing live state
  in VR; use a small helper executable instead of forcing the whole editor into
  the headset; keep profiles and live tuning distinct from the overlay host.
- Interesting implementation choices:
  `omni-profile-editor/src/main/vrOverlay.ts`
  shows the bridge from the desktop app into the helper process, while
  `profileManager.ts`
  makes the persisted profile and live-update boundary explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  specific to one tuning workflow, but unusually clear as a
  `desktop-first tool with VR presence` donor.
- What to inspect next:
  keep it visible whenever a future branch needs
  `live tuning surface driven from a richer desktop editor`.

## `OpenShock/OVR-Shock`

- GitHub:
  [OpenShock/OVR-Shock](https://github.com/OpenShock/OVR-Shock)
- What it is:
  a modern `Qt` and C++ overlay for controlling `OpenShock` devices from inside
  VR, with saved settings, network API access, and hand-specific overlay
  behavior.
- Why it matters:
  it is the clearest donor in the repo for
  `external-device control overlay with persisted config and remote API fan-out`.
- Interesting ideas:
  treat remote-device control as an overlay-native workflow; persist device and
  behavior settings cleanly; switch handedness or placement as part of the
  overlay UX rather than an afterthought.
- Interesting implementation choices:
  `src/api_client.cpp`
  shows the remote-device boundary,
  `src/config.cpp`
  captures the persisted state model, and
  `src/vrwidget.cpp`
  makes the overlay-side UI concrete.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  hardware-specific, but still a strong donor for any
  `external device controlled from VR` branch.
- What to inspect next:
  keep it visible whenever a future branch needs
  `overlay as a remote-device control panel`.

## `OpenShock/VROverlay`

- GitHub:
  [OpenShock/VROverlay](https://github.com/OpenShock/VROverlay)
- What it is:
  an older Unity-based overlay in the same product direction, useful mainly as
  a lineage comparison node against the newer `OVR-Shock`.
- Why it matters:
  it helps clarify which parts of the device-control branch stayed stable and
  which parts moved into a stronger modern host.
- Interesting ideas:
  use Unity as the overlay shell; keep initialization of the external device
  link and overlay helper explicit; expose the earlier product framing before
  the `Qt` rewrite.
- Interesting implementation choices:
  `Assets/InitShockLink.cs`
  plus `EasyOpenVROverlayForUnity.cs`
  and `Control.cs`
  show the older
  `Unity overlay helper -> device link -> control surface`
  structure.
- Code donor value:
  medium.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  best treated as a `Partially studied` lineage node, not as the main donor
  over `OVR-Shock`.
- What to inspect next:
  revisit only if a future pass needs a sharper lineage comparison between the
  older Unity stack and the current `Qt` implementation.

## Main takeaways from Wave 59

- `Embodied control overlays` are clearer when split into:
  - `locomotion overlay that maps body motion into avatar intent`
  - `desktop editor plus live VR tuning surface`
  - `external-device control overlay with persisted config and remote API`
  - `older lineage node that explains the branch's evolution`
- The strongest lesson from this wave is that some of the best VR surfaces are
  not display-first. They are `control-first`, with the overlay acting as a
  manipulation surface for bodily or external state.
- Another strong lesson is that `desktop-first editor plus native VR helper`
  can be a cleaner product split than forcing all tuning UX into the headset.

## Reusable methods clarified by this wave

- `Embodied locomotion overlay that maps gaze or tracker motion into avatar-control intent`
- `Desktop editor paired with a native VR helper over a framed streaming protocol`
- `External-device control overlay with persisted config, hand switching, and remote API fan-out`

## Recommended next moves after this wave

1. Treat `bikeheadvr` as the clearest donor for
   `controllerless embodied locomotion surface`.
2. Keep `Omni-Tune` visible whenever `VR-apps-lab` needs a
   `desktop editor with live in-headset tuning`.
3. Treat `OVR-Shock` as the main donor for
   `overlay-native remote-device control`.
4. Keep `OpenShock/VROverlay` as an honest lineage node rather than another
   equally strong current donor.
