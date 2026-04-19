# VR Projects Wave 23: Glove Platforms, Poser Stacks, and Nonstandard Hardware Bridge Drivers

- Date: `2026-04-19`
- Goal: add the next serious GitHub discovery wave for repositories that were
  not yet represented deeply enough in `VR-apps-lab`, focusing on
  `glove platforms`, `poser stacks`, and `nonstandard hardware bridge drivers`.

## Why this wave exists

The repository already had a useful `driver tutorial` family, but it still
needed denser examples where:

- `firmware`, `transport`, `sidecar`, and `driver` form one public ecosystem;
- an external `poser` or `binding API` becomes the real device-ingress surface;
- unusual control hardware or foreign VR frameworks still produce reusable
  bridge-driver lessons.

This wave exists to make `custom hardware ecosystems` a stronger architecture
track inside `VR-apps-lab`.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with glove, poser, remote-relay, and compatibility-bridge
   family queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `LucidVR/opengloves-driver` | Strongest current glove-specific SteamVR driver donor in the repo |
| `LucidVR/lucidgloves` | Matching firmware and hardware ecosystem for the same glove family |
| `HoboVR-Labs/hobo_vr` | Rare public example of an explicit external poser protocol with language bindings |
| `Copprhead/hotas-vr-controller` | Good niche reference for controller relocation and click interception around real cockpit hardware |
| `SophiaH67/soph_wireless` | Clean relay-driver idea for registering remote trackers over UDP |
| `SophiaH67/soph_wireless_transmitter` | Tiny but useful companion sender that makes the relay architecture explicit |
| `OSVR/SteamVR-OSVR` | Historical but still valuable compatibility bridge between a foreign VR framework and SteamVR |
| `terminal29/OSVR-SteamVR-Bridge` | Smaller comparison node that shows the same family in a much thinner form |
| `r57zone/Razer-Hydra-SteamVR-driver` | Good legacy peripheral bridge with device mapping, config, and monitor tooling |

## Secondary candidates surfaced in the same wave

| Project | Why it was not promoted further yet |
|---|---|
| `puresoul/Barebone` | Still useful, but better kept as a thinner synthetic-controller comparison node rather than a core custom-hardware ecosystem donor |
| `TrueOpenVR/SteamVR-TrueOpenVR` | Still interesting as an external DLL-fed bridge, but not as strong as the clearer glove and poser stacks in this pass |

## Deep-pass notes by project

## `LucidVR/opengloves-driver`

- GitHub:
  [LucidVR/opengloves-driver](https://github.com/LucidVR/opengloves-driver)
- What it is:
  a SteamVR driver ecosystem for DIY gloves.
- Why it matters:
  it is the clearest public donor in the repository for a modern
  `multi-transport custom-device provider with sidecar control surface`.
- Interesting ideas:
  separate driver, server, service layers, and overlay; keep multiple transport
  paths visible; treat glove support as a platform rather than one hardcoded
  serial device.
- Interesting implementation choices:
  the driver tree splits into `device`, `services`, and `hand_tracking`
  modules; the repo also includes `server/src/communication` and a dedicated
  `driver/overlay/main.cpp`, which makes the operational split explicit.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  custom hardware ecosystem complexity is real; the full stack is broader than
  a simple OpenVR driver tutorial.
- What to inspect next:
  where the driver/server/overlay boundaries are stable enough to reuse and how
  transport discovery is normalized across hardware variants.

## `LucidVR/lucidgloves`

- GitHub:
  [LucidVR/lucidgloves](https://github.com/LucidVR/lucidgloves)
- What it is:
  the firmware, hardware, and build ecosystem paired with the LucidVR glove
  driver stack.
- Why it matters:
  it turns the LucidVR line from `one driver repo` into a full
  `firmware-plus-driver co-designed custom device ecosystem`.
- Interesting ideas:
  support multiple communication paths; make encoding formats explicit; keep
  gesture, haptics, and input-manager layers visible inside the firmware.
- Interesting implementation choices:
  the firmware tree contains `Serial`, `BTSerial`, and `WIFISerial`
  communication layers; `AlphaEncoding` and `LegacyEncoding`; and controller
  subsystems for `Gesture`, `Haptics`, and `InputManager`.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  firmware donor value is strongest when studied together with the matching
  driver ecosystem rather than in isolation.
- What to inspect next:
  how the protocol and capability model align with `opengloves-driver`, and
  whether a future reuse plan should document the full LucidVR ecosystem.

## `HoboVR-Labs/hobo_vr`

- GitHub:
  [HoboVR-Labs/hobo_vr](https://github.com/HoboVR-Labs/hobo_vr)
- What it is:
  a custom SteamVR stack organized around an explicit external `poser` model and
  public bindings.
- Why it matters:
  it is the strongest donor in the repo for `external driver protocol with
  language bindings and poser processes`.
- Interesting ideas:
  expose a `virtualreality` API; support `cpp` and `python` bindings; let
  external programs act as device posers; keep Linux support explicit.
- Interesting implementation choices:
  the repo includes `bindings/cpp/virtualreality`, `bindings/python/virtualreality`,
  many poser examples under `bindings/python/examples/`, and driver reference
  code under `driver/src/ref/`.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  this is a prototyping-heavy stack rather than a polished end-user utility.
- What to inspect next:
  how stable the poser contract is in practice and whether its external API
  shape could inspire future `VR-apps-lab` bridge experiments.

## `Copprhead/hotas-vr-controller`

- GitHub:
  [Copprhead/hotas-vr-controller](https://github.com/Copprhead/hotas-vr-controller)
- What it is:
  a niche bridge that repositions VR controllers onto real cockpit controls and
  supplements them with external click devices.
- Why it matters:
  it is a rare public example of `tracked-controller relocation via config
  offsets and click interception`.
- Interesting ideas:
  strap controllers to a hand, arm, or cockpit context; remap grip and trigger
  through external click devices; let real-world hardware define the comfort
  model rather than default controller ergonomics.
- Interesting implementation choices:
  the code makes `ControllerOffset`, `Hooking`, and `InterfaceHookInjector`
  explicit; `driver_hotas.ini` shows that config-driven offset and behavior
  shaping are central to the design.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  very niche, but that narrowness is part of why it is a useful micro-donor.
- What to inspect next:
  how robust the hook surface is across SteamVR versions and whether the offset
  model could generalize into other attachment-based utility tools.

## `SophiaH67/soph_wireless`

- GitHub:
  [SophiaH67/soph_wireless](https://github.com/SophiaH67/soph_wireless)
- What it is:
  a SteamVR driver that listens for UDP packets and registers remote trackers
  from another SteamVR instance.
- Why it matters:
  it is a clean `remote tracker relay` donor with a very explicit two-process
  architecture.
- Interesting ideas:
  keep the receiver small; let another machine or instance act as the sender;
  turn remote tracker state into local SteamVR devices over a lightweight UDP
  path.
- Interesting implementation choices:
  the repo includes `controller_device.*`, `device_provider.*`,
  `hmd_driver_factory.cpp`, and `packet.h`, which makes the protocol and driver
  boundary easy to study.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  narrow protocol and deployment assumptions; strongest when studied together
  with its paired transmitter repo.
- What to inspect next:
  compare it with generic WebSocket and named-pipe tracker-ingress drivers to
  see where the relay pattern is genuinely different.

## `SophiaH67/soph_wireless_transmitter`

- GitHub:
  [SophiaH67/soph_wireless_transmitter](https://github.com/SophiaH67/soph_wireless_transmitter)
- What it is:
  the paired sender utility for `soph_wireless`.
- Why it matters:
  even though it is tiny, it makes the relay architecture explicit as
  `sender + packet contract + receiver driver`.
- Interesting ideas:
  keep the transmitter separate from the driver; make packet ownership visible;
  avoid hiding remote-state capture inside the receiver.
- Interesting implementation choices:
  the repo is small, but `packet.h` and `soph_wireless_transmitter.cpp` are
  enough to make the sender side of the design concrete.
- Code donor value:
  medium.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  too small to stand as a major donor alone.
- What to inspect next:
  treat it mainly as the paired half of `soph_wireless`, not as an independent
  product direction.

## `OSVR/SteamVR-OSVR`

- GitHub:
  [OSVR/SteamVR-OSVR](https://github.com/OSVR/SteamVR-OSVR)
- What it is:
  a compatibility bridge between the `OSVR` framework and SteamVR.
- Why it matters:
  it is still a useful donor for `foreign framework -> SteamVR compatibility
  driver` design.
- Interesting ideas:
  map an external VR framework's HMD, tracked devices, display, and references
  into SteamVR components instead of building an isolated custom device path.
- Interesting implementation choices:
  the source exposes `ServerDriver_OSVR`, `OSVRTrackedHMD`,
  `OSVRTrackedDevice`, `OSVRDisplay`, and `OSVRTrackingReference`, making the
  bridge architecture easy to read.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  high.
- Caveats:
  historical stack and older ecosystem assumptions reduce its current product
  relevance, but not its architecture value.
- What to inspect next:
  compare with thinner compatibility bridges to isolate the minimum useful
  framework-to-SteamVR mapping pattern.

## `terminal29/OSVR-SteamVR-Bridge`

- GitHub:
  [terminal29/OSVR-SteamVR-Bridge](https://github.com/terminal29/OSVR-SteamVR-Bridge)
- What it is:
  a much smaller compatibility-bridge variant for OSVR to SteamVR.
- Why it matters:
  it is a useful comparison node because it exposes the same family with much
  less platform baggage.
- Interesting ideas:
  use hardcoded alias mapping such as `/controller1/pose` and `/hmd/pose`;
  support a monitor-backed headset path; keep the bridge compact.
- Interesting implementation choices:
  the donor value is mostly in the direct alias-mapping model and the thinner
  bridge framing rather than in deep subsystem breadth.
- Code donor value:
  medium.
- Product reference value:
  low-medium.
- Architecture reference value:
  medium.
- Caveats:
  smaller and less comprehensive than `SteamVR-OSVR`.
- What to inspect next:
  keep it as a comparison node for `minimum useful compatibility bridge`.

## `r57zone/Razer-Hydra-SteamVR-driver`

- GitHub:
  [r57zone/Razer-Hydra-SteamVR-driver](https://github.com/r57zone/Razer-Hydra-SteamVR-driver)
- What it is:
  a legacy bridge that maps `Razer Hydra` hardware into SteamVR controller
  semantics.
- Why it matters:
  it is a good peripheral-integration reference where device mapping, configs,
  and helper tools matter as much as the core driver.
- Interesting ideas:
  map Hydra controls onto Vive or Index-style semantics; pair the driver with a
  monitor tool; keep the bridge useful alongside other DIY HMD paths.
- Interesting implementation choices:
  `driver_hydra.cpp`, `resources/input/*`, and `tools/hydra_monitor/*` show the
  split between runtime-side device mapping and user-side helper tooling.
- Code donor value:
  medium-high.
- Product reference value:
  medium.
- Architecture reference value:
  medium-high.
- Caveats:
  historical hardware target, but still a clear bridge-driver lesson.
- What to inspect next:
  compare its helper-tool and config surface with other peripheral bridges in
  the repo.

## Main takeaways from Wave 23

- `Custom hardware ecosystem` is now clearer as more than just
  `write a SteamVR driver`.
- The strongest split inside the family is:
  - `firmware plus driver ecosystem`
  - `external poser protocol with bindings`
  - `niche physical-device relocation bridge`
  - `remote tracker relay pair`
  - `foreign framework compatibility bridge`
- Small companion repos can still matter when they make the system boundary
  explicit, as seen in `soph_wireless_transmitter`.

## Reusable methods clarified by this wave

- `External driver protocol with language bindings and poser processes`
- `Firmware-plus-driver co-designed custom device ecosystem`
- `Tracked-controller relocation via config offsets and click interception`

## Recommended next moves after this wave

1. Keep the `LucidVR` line as the strongest current glove ecosystem donor in
   the repo.
2. Promote `hobo_vr` as the clearest public reference for explicit external
   poser protocols and bindings.
3. Keep `soph_wireless` visible as a distinct relay-driver pattern rather than
   folding it into generic tracker-ingress notes.
4. Use `SteamVR-OSVR`, `OSVR-SteamVR-Bridge`, and `Razer-Hydra-SteamVR-driver`
   mainly as compatibility and peripheral-bridge references, not as new product
   directions.
