# VR Projects Wave 40: VRChat Chatbox, STT, and Text-Surface Sidecars

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `VRChat chatbox workflows`, `speech-to-text sidecars`, and
  `avatar text-surface utilities`.

## Why this wave exists

`VR-apps-lab` already had communication helpers, captions, and social sidecar
references, but one specific branch was still under-modeled:

- chatbox composers that squeeze multiple live status sources into a bounded
  text surface;
- speech-to-avatar text systems that rely on parameter grids and generated
  animators rather than a plain overlay;
- keyboard or textbox utilities that make chat entry possible without returning
  to a desktop monitor.

This wave exists to make `VRChat chatbox, STT, and text-surface sidecars`
clearer inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with VRChat chatbox, STT, textbox, and overlay-keyboard
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `BoiHanny/vrcosc-magicchatbox` | Strong donor for a modular multi-status chatbox composer with a broad desktop host |
| `yum-food/TaSTT` | Strong donor for STT-to-avatar text surfaces driven by generated parameter grids and animator assets |
| `cyberkitsune/vrc-osc-scripts` | Focused micro-script donor for rate-limited chatbox updates and small VRChat OSC helpers |
| `nyakowint/xsoverlay-keyboard-osc` | Strong donor for patching an existing overlay keyboard into OSC chat input instead of rebuilding a keyboard from scratch |
| `I5UCC/VRCTextboxOSC` | Thin donor for a focused desktop textbox utility with hotkey, trimming, and always-on-top behavior |
| `Lioncat6/OSC-Chat-Tools` | Product-rich donor for a monolithic but useful status-composition desktop surface |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `I5UCC/VRCTextboxSTT` | Already tracked from earlier waves, and the stronger new donors in this wave already clarify STT, chatbox, and textbox-sidecar patterns more cleanly |

## Deep-pass notes by project

## `BoiHanny/vrcosc-magicchatbox`

- GitHub:
  [BoiHanny/vrcosc-magicchatbox](https://github.com/BoiHanny/vrcosc-magicchatbox)
- What it is:
  a broad WPF desktop companion that assembles multiple status modules into
  VRChat chatbox output under a fixed text budget.
- Why it matters:
  it is the clearest donor in the repo for
  `character-budgeted modular chatbox composition`.
- Interesting ideas:
  treat the chatbox like a compact utility dashboard; gather time, media,
  network, and sensor data through separate modules; keep formatting and output
  assembly in one reusable controller.
- Interesting implementation choices:
  `OSCController.cs`,
  `IntelliChatModule.cs`, and
  `MainWindow.xaml.cs`
  make the `module timer -> aggregate status fields -> bounded chat payload`
  flow explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  broad scope and a custom source-available posture make it a stronger idea
  donor than a clean drop-in code donor.
- What to inspect next:
  revisit only if a future pass needs a narrower comparison of module
  boundaries, provider extensibility, or licensing constraints.

## `yum-food/TaSTT`

- GitHub:
  [yum-food/TaSTT](https://github.com/yum-food/TaSTT)
- What it is:
  an archived but still strong desktop-plus-avatar system that turns local
  speech into avatar-visible text through generated animator and parameter
  assets.
- Why it matters:
  it is the clearest donor in the repo for
  `generated avatar text surface driven by block-addressed OSC parameters`.
- Interesting ideas:
  separate speech capture, SteamVR button polling, and avatar-side rendering;
  generate the Unity animator scaffolding instead of hand-authoring large text
  grids; treat avatar parameters as a text display bus.
- Interesting implementation choices:
  `app/stt.py`,
  `app/steamvr.py`, and
  `GenerateTextAnimator.cs`
  make the `local STT -> page text into parameter blocks -> avatar animator
  surface` flow explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  archived status limits product freshness, but the construction method remains
  unusually clear and reusable.
- What to inspect next:
  keep it visible whenever a future branch needs
  `speech-to-avatar text rendering` rather than only chatbox emission.

## `cyberkitsune/vrc-osc-scripts`

- GitHub:
  [cyberkitsune/vrc-osc-scripts](https://github.com/cyberkitsune/vrc-osc-scripts)
- What it is:
  a set of small Python helpers that push subtitles, now-playing text, and
  related compact data into VRChat via `OSC`.
- Why it matters:
  it is a strong donor for the `micro-utility` end of the chatbox family.
- Interesting ideas:
  do one narrow thing well; keep scripts small; account for chatbox rate limits;
  use `OSCQuery` where appropriate instead of hardcoding everything.
- Interesting implementation choices:
  `VRCSubs/vrcsubs.py` and
  `VRCNowPlaying/vrcnowplaying.py`
  show `focused provider -> compact formatter -> chatbox sender` with very
  little product overhead.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  these are deliberately thin scripts, so they teach more about
  `small useful tools` than about broader platform structure.
- What to inspect next:
  reuse as a reference whenever a future utility only needs one precise chatbox
  or avatar-facing output path.

## `nyakowint/xsoverlay-keyboard-osc`

- GitHub:
  [nyakowint/xsoverlay-keyboard-osc](https://github.com/nyakowint/xsoverlay-keyboard-osc)
- What it is:
  a BepInEx and Harmony plugin that patches XSOverlay's keyboard flow so it can
  push text into VRChat chatbox `OSC`.
- Why it matters:
  it is the clearest donor in the repo for
  `patch an existing overlay keyboard instead of building a new one`.
- Interesting ideas:
  add a chat mode to an existing keyboard surface; patch UI affordances in
  place; use a small plugin to turn a general overlay into a focused text-entry
  tool.
- Interesting implementation choices:
  `Plugin.cs`,
  `Patches.cs`, and
  `ToggleChatButton.cs`
  make the `existing keyboard host -> injected toggle/button -> OSC chat send`
  path explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  the donor value is strongest when `VR-apps-lab` wants to augment an existing
  utility host rather than own the whole keyboard surface.
- What to inspect next:
  keep it visible whenever a future path needs `overlay patching over an
  existing VR UI surface`.

## `I5UCC/VRCTextboxOSC`

- GitHub:
  [I5UCC/VRCTextboxOSC](https://github.com/I5UCC/VRCTextboxOSC)
- What it is:
  a thin WPF textbox app that sends chat text through `OSC` with support for
  focus hotkeys, overflow trimming, and always-on-top behavior.
- Why it matters:
  it is one of the clearest product references for
  `thin utility app with one strong user value`.
- Interesting ideas:
  keep the UI tiny; prioritize quick focus, clear text limits, and minimal
  friction over broader platform scope; register as a VR-adjacent utility
  without turning into a full overlay host.
- Interesting implementation choices:
  `MainWindow.xaml.cs`
  shows a compact `desktop textbox -> trim or page text -> send OSC` loop with
  product-minded focus behavior.
- Code donor value:
  medium.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  intentionally narrow scope means the main lesson is product sharpness, not
  architectural breadth.
- What to inspect next:
  treat it as the cleanest comparison node whenever a future branch needs a
  `single-purpose text utility`.

## `Lioncat6/OSC-Chat-Tools`

- GitHub:
  [Lioncat6/OSC-Chat-Tools](https://github.com/Lioncat6/OSC-Chat-Tools)
- What it is:
  a monolithic but product-rich desktop app that composes many live status
  sources into chatbox output and related helper surfaces.
- Why it matters:
  it complements `vrcosc-magicchatbox` by showing the
  `feature-rich monolithic status composer` side of the family.
- Interesting ideas:
  treat the chatbox as a dense status surface; combine Pulsoid, media, system,
  and web helpers; allow layout-driven composition instead of one hardcoded
  output path.
- Interesting implementation choices:
  `osc-chat-tools.py`
  centralizes provider handling, layout composition, and helper services in one
  script-heavy desktop host.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium.
- Caveats:
  monolithic structure makes it a stronger product reference than a clean
  architectural donor.
- What to inspect next:
  use it as a comparison node whenever a future branch needs
  `broad product framing` rather than the cleanest modular implementation.

## Main takeaways from Wave 40

- `VRChat text tooling` is its own utility family, not just an accessory to
  captions or generic social overlays.
- The strongest split in this family is:
  - `modular multi-status chatbox composer`
  - `avatar text surface generated from parameter grids`
  - `micro-script helpers for one bounded text output`
  - `patched overlay keyboard`
  - `thin textbox utility`
  - `feature-rich monolithic status composer`
- The most reusable lesson is that `text entry and text output are different
  product problems`:
  - composing useful text under a character budget
  - rendering longer text through avatar parameters
  - patching existing input surfaces instead of rebuilding them
  - keeping thin utilities intentionally small

## Reusable methods clarified by this wave

- `Character-budgeted chatbox composition over modular desktop status providers`
- `Generated avatar text surface over block-addressed OSC parameter pages`
- `Existing overlay keyboard patched into VRChat chatbox input`

## Recommended next moves after this wave

1. Treat `TaSTT` as the main donor whenever a future branch needs
   `speech-to-avatar text surfaces` instead of plain captions.
2. Keep `vrcosc-magicchatbox` visible as the strongest broad donor for
   `modular chatbox composition under a fixed text budget`.
3. Keep `xsoverlay-keyboard-osc` as the clearest example of
   `overlay patch micro-tooling` applied to text entry.
4. Use `VRCTextboxOSC` and `vrc-osc-scripts` whenever a future idea should stay
   intentionally narrow instead of becoming another broad companion platform.
