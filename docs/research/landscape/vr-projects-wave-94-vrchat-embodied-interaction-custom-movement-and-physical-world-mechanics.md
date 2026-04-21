# VR Projects Wave 94: VRChat Embodied Interaction, Custom Movement, and Physical World Mechanics

- Date: `2026-04-21`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat embodied interaction`, `custom movement`, and
  `physical world-mechanics prefabs`.

## Why this wave exists

`VR-apps-lab` already had better coverage of utility UI and runtime helper
systems than of:

`how creator worlds implement physical controls, grapples, movement overrides, doors, or vehicles when the user should feel like they are touching or driving something instead of just pressing a UI button`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with VRChat interaction, grapple, movement, and vehicle
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `Janooba/immersive-interactions` | Strong donor for physics-first buttons, switches, and avatar-bone interaction surfaces |
| `squiddingme/UdonTether` | Strong donor for grapple physics, auto-aim, and swing or rigidbody split |
| `Nestorboy/NUMovement` | Strong donor for an extensible custom VRChat-like movement controller |
| `esnya/UdonDoor` | Strong donor for a narrow but elegant pickup-driven physical door |
| `kurotori4423/KurotoriUdonKart` | Strong reference for motion-controller vehicle handling and seat or throttle split |

## Deep-pass notes by project

## `Janooba/immersive-interactions`

- GitHub:
  [Janooba/immersive-interactions](https://github.com/Janooba/immersive-interactions)
- What it is:
  a VCC-style package of physics-first buttons, switches, levers, and tracked
  hand helpers for VRChat worlds.
- Why it matters:
  it is the clearest donor in this wave for
  `world interaction that starts from avatar-bone colliders instead of from plain Interact events`.
- Interesting ideas:
  build a reusable local-player skeleton of colliders; let buttons and switches
  sleep when idle; keep desktop fallback separate from physics interaction; let
  world authors configure rich event routing, tint, texture, and ownership
  transfer in prefab surfaces.
- Interesting implementation choices:
  `PlayerSkeletonInfo.cs`
  constructs tracked bone colliders and falls back when hands are unavailable;
  `Pressable_Button.cs`
  combines collision filtering, cooldown, ownership transfer, network sync,
  fallback clicks, tint or texture states, and sleeping logic; `Flippable_Switch.cs`
  extends the same model into rotational controls plus optional lever handles.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the package is broad enough that a future pass could still peel apart button,
  switch, and lever lineages more deeply.
- What to inspect next:
  revisit when `VR-apps-lab` needs a stronger
  `physics-first control surface toolkit`
  reference.

## `squiddingme/UdonTether`

- GitHub:
  [squiddingme/UdonTether](https://github.com/squiddingme/UdonTether)
- What it is:
  a grappling or tether system that can swing the player or manipulate lighter
  rigidbodies through the same tether abstraction.
- Why it matters:
  it is the clearest donor in this wave for
  `grapple locomotion implemented as a small focused runtime controller`.
- Interesting ideas:
  auto-aim by combining raycast and spherecast passes; keep tether properties in
  a shareable config object; switch between player swing and rigidbody
  manipulation based on target mass.
- Interesting implementation choices:
  `TetherController.cs`
  handles detection, tether state, spring projection, unwind logic, and the
  player-versus-rigidbody split; `TetherProperties.cs`
  exposes the tuning surface for force, detection, and input thresholds.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is intentionally focused and does not attempt a broader locomotion
  framework around the tether mechanic.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `grapple or swing locomotion`
  donor.

## `Nestorboy/NUMovement`

- GitHub:
  [Nestorboy/NUMovement](https://github.com/Nestorboy/NUMovement)
- What it is:
  a custom movement package for VRChat worlds with an abstract base controller,
  platform interaction modes, jump shaping, slope handling, and movement
  extension points.
- Why it matters:
  it is the clearest donor in this wave for
  `creator-side custom movement as a reusable framework instead of one monolithic script`.
- Interesting ideas:
  separate a cached base controller from a concrete movement policy; expose many
  movement behaviours as overridable or configurable pieces; keep debug drawing
  and collider helpers in the package so iteration stays practical.
- Interesting implementation choices:
  `AbstractMovement.cs`
  centralizes controller, input, gravity, player-state, and hit buffering;
  `NUMovement.cs`
  layers ground, walk, jump, gravity, platform interaction, stance handling,
  and VR offset logic on top of that substrate.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  very high.
- Caveats:
  the framework is broad and designed for extension, so one pass still does not
  exhaust all derived-class and helper possibilities.
- What to inspect next:
  revisit when `VR-apps-lab` needs a stronger
  `custom movement framework and extension surface`
  reference.

## `esnya/UdonDoor`

- GitHub:
  [esnya/UdonDoor](https://github.com/esnya/UdonDoor)
- What it is:
  an interactable physical door prefab built around a pickup handle, signed
  angle tracking, and spring or drag motion.
- Why it matters:
  it is the clearest narrow donor in this wave for
  `physical hinge interaction as a small reusable prefab`.
- Interesting ideas:
  drive the hinge target from pickup position projected onto the door axis;
  keep door motion, grab state, and sound logic inside one compact controller;
  sync the angle rather than the whole transform behaviour.
- Interesting implementation choices:
  `DoorController.cs`
  splits grab state, hinge-angle math, synced door angle, and audio cue
  triggers while using gizmo hints for setup.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  it is intentionally narrow and does not try to generalize into a larger
  interaction package.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `pickup-driven hinge or door`
  donor.

## `kurotori4423/KurotoriUdonKart`

- GitHub:
  [kurotori4423/KurotoriUdonKart](https://github.com/kurotori4423/KurotoriUdonKart)
- What it is:
  a kart system for VRChat with motion-controller steering, desktop controls,
  seat height adjustment, wheel visuals, and time-attack support.
- Why it matters:
  it is the clearest reference in this wave for
  `physical vehicle control that splits seat, handle, throttle, and visual layers`.
- Interesting ideas:
  derive steering from two tracked hand positions on a virtual handle; keep
  throttle, seat, state, and visual systems separate; support both VR and
  desktop input paths under one vehicle shell.
- Interesting implementation choices:
  `UdonCarSystem.cs`
  owns speed, steering, brake, VR versus desktop control, and wheel collider
  application; `VehicleHandle.cs`
  derives handle angle from the two hand transforms and updates a synced
  steering surface.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  the repo is broader than the single files inspected here and some of the most
  interesting lineage sits in seat, time-attack, and state-side companions.
- What to inspect next:
  revisit when `VR-apps-lab` needs a stronger
  `controller-steered creator vehicle`
  reference.

## Main takeaways from Wave 94

- `VRChat physical world mechanics`
  now splits more cleanly into:
  - physics-first control surface toolkits;
  - narrow grapple locomotion helpers;
  - extensible movement frameworks;
  - compact hinge or door prefabs;
  - controller-steered vehicle rigs.
- The strongest lesson from this wave is that
  `embodied interaction`
  often needs a dedicated runtime representation of hands, bodies, or handles,
  not just extra events.
- Another strong lesson is that
  `movement and mechanics donors`
  get more reusable when their control surface and configuration layer are
  separated from the actual physical update loop.

## Reusable methods clarified by this wave

- `Local-player bone-collider skeleton driving physics-first buttons and switches with fallback mode`
- `Sleep-aware manual-sync control surface with collider filtering, cooldowns, ownership transfer, and event suffixing`
- `Grapple or tether controller with spherecast auto-aim, spring projection, and optional rigidbody manipulation`
- `Extensible custom movement controller with VRChat-like inputs, platform inheritance, and ground or stance abstraction`
- `Pickup-driven hinge door with signed-angle target, spring or drag motion, and synced sound cues`
- `Motion-controller steering kart rig with seat, handle, throttle, and visual state split`

## Recommended next moves after this wave

1. Keep `immersive-interactions` visible as one of the strongest
   `physics-first creator interaction`
   donors in the repo.
2. Treat `UdonTether` as a compact but high-value
   `grapple locomotion`
   donor.
3. Use `NUMovement` whenever future work needs a deeper
   `movement framework and extension point`
   reference.
4. Keep `UdonDoor` visible as a strong narrow donor for
   `pickup-driven hinge interaction`.
5. Revisit `KurotoriUdonKart` whenever future work needs a stronger
   `vehicle control and seat-state workflow`
   reference.
