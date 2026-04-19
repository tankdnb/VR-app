# VR Projects Wave 29: Hand, Palm, Radial, and Quick-Access Menus

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `hand menus`, `palm menus`, `radial menus`, and `quick-access VR surfaces`.

## Why this wave exists

`VR-apps-lab` already had many references for overlays and tool windows, but it
still needed a stronger donor set for the first interaction step that makes
those utilities usable:

- how the menu is revealed;
- how commands stay close to the hand without becoming noisy;
- how a small launcher graduates into a richer panel or control surface.

This wave exists to make `quick-access menu UX in VR` a stronger method family
inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with hand-menu, palm-menu, radial-menu, and quick-menu
   family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `NovaUI-Unity/XRHandMenuSample` | Strongest palm-up launcher donor with a separate popup panel target |
| `Housz/VRMenuDesigner` | Best menu-archetype toolkit covering default, radial, ring, and modifier flows |
| `Oyshoboy/RadialMenuVR` | Useful minimal radial-selection donor with hover scaling and auto-hide |
| `yusufalibrahim1994/UnityXR-Physicalized-Radial-Menu` | Distinct donor for turning menu selection into real interactable handoff |
| `auroreRakoto/XR-UI-Prototype` | Small contextual menu-to-secondary-panel comparison node |

## Deep-pass notes by project

## `NovaUI-Unity/XRHandMenuSample`

- GitHub:
  [NovaUI-Unity/XRHandMenuSample](https://github.com/NovaUI-Unity/XRHandMenuSample)
- What it is:
  a hand-menu sample where a palm-up launcher opens richer panels at a separate
  popup anchor.
- Why it matters:
  it is the strongest donor in the repo for
  `palm-up launcher -> richer world-space panel` flow.
- Interesting ideas:
  reveal the launcher only when palm orientation relative to the head passes a
  threshold; hide the launcher while a panel is active; keep the quick launcher
  on the hand but show heavier content at a more readable popup location.
- Interesting implementation choices:
  `PanelUIController.cs` and `HandLauncher.cs` make the palm-threshold gating,
  hand-anchor placement, and scrollable launcher behavior explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  most useful as an interaction pattern, not as a finished utility product.
- What to inspect next:
  compare it directly with `mr-example-meta-openxr` and MRTK hand menus to
  isolate what belongs to the launcher pattern versus framework-level plumbing.

## `Housz/VRMenuDesigner`

- GitHub:
  [Housz/VRMenuDesigner](https://github.com/Housz/VRMenuDesigner)
- What it is:
  a Unity toolkit for generating and modifying default, radial, ring, and
  Windows-style VR menus.
- Why it matters:
  it is the strongest donor in the repo for
  `menu-archetype generator with editor-side creation and modification`.
- Interesting ideas:
  treat menu type as a reusable archetype; expose creators and modifiers in the
  editor; bridge radial and ring menus instead of treating them as unrelated
  widgets.
- Interesting implementation choices:
  `Creator.cs`, `Modifier.cs`, `RadialMenu.cs`, `RingMenu.cs`, `RingLayout.cs`,
  and `Radial2Ring.cs` make the `tooling layer -> menu archetype` split easy
  to inspect.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  oriented toward Unity authoring workflows more than runtime-only menu logic.
- What to inspect next:
  reuse it whenever a future `VR-apps-lab` prototype needs menu archetypes and
  not only one hand-crafted radial component.

## `Oyshoboy/RadialMenuVR`

- GitHub:
  [Oyshoboy/RadialMenuVR](https://github.com/Oyshoboy/RadialMenuVR)
- What it is:
  a small runtime radial menu with simple hover and selection behavior.
- Why it matters:
  it is a good donor for the lightweight end of the radial-menu family.
- Interesting ideas:
  choose the nearest menu item based on hand or mouse position; scale the
  hovered choice; auto-hide based on distance so the menu feels temporary
  instead of sticky.
- Interesting implementation choices:
  `Scripts/RadialMenuHandler.cs` keeps the full open, hover, scale, and close
  loop compact enough to understand quickly.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  medium.
- Caveats:
  intentionally simple and narrow.
- What to inspect next:
  keep it as the minimum viable comparison donor whenever a later wave wants to
  strip radial menus down to the smallest useful behavior set.

## `yusufalibrahim1994/UnityXR-Physicalized-Radial-Menu`

- GitHub:
  [yusufalibrahim1994/UnityXR-Physicalized-Radial-Menu](https://github.com/yusufalibrahim1994/UnityXR-Physicalized-Radial-Menu)
- What it is:
  an XR radial menu that opens on thumbstick input and resolves selection by
  placing a real interactable into the user's hand.
- Why it matters:
  it is the clearest donor in the repo for
  `physicalized radial selection that materializes interactables`.
- Interesting ideas:
  open and close the menu with input actions; arrange real selection targets
  around the hand; use direct-interactor proximity for selection; convert the
  chosen item into a forced hand selection rather than a detached UI result.
- Interesting implementation choices:
  `Assets/RadialMenuXR.cs` and the `XRInteractionManager.ForceSelect(...)`
  usage make the bridge from menu choice to interactable handoff explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  centered on item-selection flow more than generic command menus.
- What to inspect next:
  keep it visible whenever a future tool needs a menu that ends in
  `grab a tool` instead of `press a command`.

## `auroreRakoto/XR-UI-Prototype`

- GitHub:
  [auroreRakoto/XR-UI-Prototype](https://github.com/auroreRakoto/XR-UI-Prototype)
- What it is:
  a small XR UI prototype built around a main activity menu and a contextual
  secondary panel.
- Why it matters:
  it is a useful small donor for the `menu list -> detail panel` pattern.
- Interesting ideas:
  generate primary menu items dynamically; open richer explanatory content in a
  second surface; keep the first menu as navigation and the second as context.
- Interesting implementation choices:
  `ActivityMenu.cs`, `MenuBController.cs`, and `FollowHead.cs` make the primary
  list, content handoff, and head-follow behavior easy to inspect.
- Code donor value:
  medium.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  narrower and more prototype-like than the other donors in this wave.
- What to inspect next:
  use it only as a lightweight comparison node for contextual secondary-panel
  behavior.

## Main takeaways from Wave 29

- `VR menus` split into several different product patterns:
  - `palm-up launcher with detached popup panel`
  - `editor-generated menu archetype toolkit`
  - `minimal radial selector`
  - `physicalized radial handoff`
  - `menu list -> contextual secondary panel`
- The strongest menu donors teach `reveal logic` and `selection semantics`,
  not only button layout.
- Small menu projects still matter because they often isolate one valuable
  behavior more clearly than a full UI framework.

## Reusable methods clarified by this wave

- `Palm-up launcher that opens richer world-space panels at a separate popup anchor`
- `Menu-archetype generator with radial, ring, and default templates plus editor-side modifiers`
- `Physicalized radial selection that materializes actual interactables into the hand`

## Recommended next moves after this wave

1. Treat `XRHandMenuSample` as the strongest donor for quick launcher plus
   detached content panel flows.
2. Keep `VRMenuDesigner` visible whenever a future prototype needs reusable
   menu archetypes, not only one hard-coded menu.
3. Use `UnityXR-Physicalized-Radial-Menu` as the best donor for
   `menu as tool-pickup surface` behavior.
