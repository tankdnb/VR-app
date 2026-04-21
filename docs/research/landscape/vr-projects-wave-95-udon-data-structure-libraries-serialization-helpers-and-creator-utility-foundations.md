# VR Projects Wave 95: Udon Data-Structure Libraries, Serialization Helpers, and Creator Utility Foundations

- Date: `2026-04-21`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `Udon data-structure libraries`, `serialization helpers`, and
  `creator utility foundations`.

## Why this wave exists

`VR-apps-lab` already had better coverage of creator prefabs and world-side
systems than of:

`the lower-layer libraries and utility substrate that make larger Udon or creator systems tolerable to build and maintain`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with Udon collection, JSON, and utility-substrate queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `Guribo/UdonUtils` | Strong donor for a broad creator utility foundation with lifecycle, singleton, execution-order, and common helpers |
| `koyashiro/udon-list` | Strong historical donor for generic list emulation in UdonSharp |
| `koyashiro/udon-dictionary` | Strong historical donor for dictionary emulation built over list substrate |
| `koyashiro/udon-json` | Strong historical donor for JSON DOM and serializer or deserializer helpers |
| `hoke946/UArrayCollections` | Strong donor for array-pair collection emulation under UdonSharp constraints |
| `Varneon/VUdon-ArrayExtensions` | Strong donor for array-extension methods that intentionally cover the `array instead of DataList` niche |

## Deep-pass notes by project

## `Guribo/UdonUtils`

- GitHub:
  [Guribo/UdonUtils](https://github.com/Guribo/UdonUtils)
- What it is:
  a broad utility foundation for creator worlds that includes a base behaviour,
  singleton pattern, execution-order tracking, common helpers, and several
  reusable runtime components.
- Why it matters:
  it is the clearest donor in this wave for
  `creator-world utility ecosystems that need shared lifecycle, logging, and ordering substrate`.
- Interesting ideas:
  build one base behaviour that standardizes networking retries, logging, and
  setup expectations; use a singleton pattern keyed by player tags; validate
  default execution order through a custom attribute; keep common world helper
  functions in a dedicated shared module.
- Interesting implementation choices:
  `TlpBaseBehaviour.cs`
  centralizes lifecycle, networking dirty-state handling, and logging;
  `TlpSingleton.cs`
  enforces singleton identity through player tags;
  `TlpDefaultExecutionOrder.cs`
  validates target types and duplicate execution orders; `UdonCommon.cs`
  packages reusable helper logic for transform paths, player lookups, and scene
  traversal.
- Code donor value:
  high.
- Product reference value:
  high.
- Architecture reference value:
  very high.
- Caveats:
  it is a broad foundation, so a deeper future pass could still peel off task,
  event, or network-time subsystems.
- What to inspect next:
  revisit when `VR-apps-lab` needs a stronger
  `creator-world utility foundation`
  reference.

## `koyashiro/udon-list`

- GitHub:
  [koyashiro/udon-list](https://github.com/koyashiro/udon-list)
- What it is:
  an archived generic list emulation for UdonSharp that stores typed arrays plus
  size and type metadata in an `object[]` state container.
- Why it matters:
  it is the clearest historical donor in this wave for
  `container emulation before native DataList support matured`.
- Interesting ideas:
  encode a generic list as an `object[]` record with array, size, and element
  type; provide allocation, growth, copy, and range helpers that mimic list
  ergonomics on top of array storage.
- Interesting implementation choices:
  `Runtime/Core/UdonList.cs`
  builds the core object-backed container, grow logic, and range or copy
  operations rather than relying on unsupported generic collections.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  the repository is archived because native `DataList` exists now, so it is a
  historical donor and fallback reference rather than the default modern choice.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs
  `pre-native generic list emulation`
  references.

## `koyashiro/udon-dictionary`

- GitHub:
  [koyashiro/udon-dictionary](https://github.com/koyashiro/udon-dictionary)
- What it is:
  an archived dictionary emulation for UdonSharp built over two object-backed
  lists: one for keys and one for values.
- Why it matters:
  it is the clearest historical donor in this wave for
  `dictionary semantics implemented on top of simpler collection substrate`.
- Interesting ideas:
  treat key and value lists as the dictionary record; reuse list primitives for
  add, remove, and lookup; keep the public surface close enough to familiar
  dictionary usage.
- Interesting implementation choices:
  `Runtime/Core/UdonDictionary.cs`
  delegates key and value storage to `UdonList` and implements dictionary
  semantics as paired-list operations.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  high.
- Caveats:
  it is also archived in favor of native `DataDictionary`, so it is strongest as
  lineage and fallback reference.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `paired-list dictionary emulation`
  donor.

## `koyashiro/udon-json`

- GitHub:
  [koyashiro/udon-json](https://github.com/koyashiro/udon-json)
- What it is:
  an archived JSON serializer and deserializer plus JSON value model for
  UdonSharp.
- Why it matters:
  it is the clearest historical donor in this wave for
  `JSON support built before native VRCJSON became the default answer`.
- Interesting ideas:
  keep a typed JSON value model as the public author surface; build
  serializer or deserializer helpers around it; keep parse errors as string
  reports instead of exceptions that Udon cannot model cleanly.
- Interesting implementation choices:
  `Runtime/UdonJsonDeserializer.cs`
  exposes a static `TryDeserialize` surface that returns both value and error
  string instead of throwing, using a lightweight object-backed parser state.
- Code donor value:
  medium-high.
- Product reference value:
  high.
- Architecture reference value:
  medium-high.
- Caveats:
  the repo is archived in favor of `VRCJSON`, so it is best used as a historical
  donor and fallback reference.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `pre-native JSON DOM and parser`
  reference.

## `hoke946/UArrayCollections`

- GitHub:
  [hoke946/UArrayCollections](https://github.com/hoke946/UArrayCollections)
- What it is:
  an UdonSharp library that emulates list, dictionary, queue, and stack
  behaviour directly on ordinary arrays.
- Why it matters:
  it is the clearest donor in this wave for
  `array-first utility collections when generics or native containers are not the desired fit`.
- Interesting ideas:
  keep everything on normal arrays and pass them by ref; model dictionaries as
  parallel key and value arrays; keep queue and stack helpers in the same
  package for a more complete array-first toolkit.
- Interesting implementation choices:
  `UDict.cs`
  shows the paired-array dictionary model directly; the package keeps
  `UList`, `UDict`, `UQueue`, and `UStack` as separate entry points instead of
  forcing one monolithic pseudo-container type.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  the README is explicit that these operations are still ordinary array copies
  and loops, so performance characteristics remain linear and need honest use.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs an
  `array-first collection emulation`
  donor.

## `Varneon/VUdon-ArrayExtensions`

- GitHub:
  [Varneon/VUdon-ArrayExtensions](https://github.com/Varneon/VUdon-ArrayExtensions)
- What it is:
  an array-extension library that adds partial `List<T>` semantics to arrays
  when creators intentionally stay on arrays instead of `DataList`.
- Why it matters:
  it is the clearest donor in this wave for
  `post-native-container array ergonomics with explicit performance caveats`.
- Interesting ideas:
  preserve array-first workflows but give them better helper ergonomics; expose
  list-like methods as extension methods; be explicit about when arrays are
  still the right choice and when they are not.
- Interesting implementation choices:
  `UdonArrayExtensions.cs`
  implements `Add`, `AddRange`, `Insert`, `Remove`, `GetRange`, `IndexOf`, and
  related helpers as plain array transformations with clear constraints.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  it is intentionally not a full container implementation and assumes creators
  already made a deliberate `array over DataList` choice.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs an
  `array extension layer over creator-world arrays`
  donor.

## Main takeaways from Wave 95

- `creator-world utility substrate`
  now splits more cleanly into:
  - broad lifecycle and execution-order foundations;
  - object-backed list emulation;
  - paired-list dictionary emulation;
  - historical JSON substrate;
  - array-first collection helpers;
  - array extension layers for post-native-container niches.
- The strongest lesson from this wave is that
  `creator substrate`
  is not just about data structures. It also includes lifecycle, logging,
  ordering, singleton identity, and common helper surfaces.
- Another strong lesson is that
  `historical donor libraries`
  remain worth keeping even after the platform adds native alternatives,
  because they still reveal good fallback shapes and abstraction strategies.

## Reusable methods clarified by this wave

- `Creator-world utility foundation with base lifecycle, singleton identity, execution-order validation, and shared common helpers`
- `Object-backed generic list emulation that stores typed array state inside a small object record`
- `Dictionary emulation over paired object-backed lists`
- `JSON DOM and parse-or-error helper surface for pre-native Udon serialization`
- `Array-first collection helpers over parallel arrays when generic containers are unavailable`
- `Array extension layer that adds partial List semantics when arrays are still the right runtime choice`

## Recommended next moves after this wave

1. Keep `UdonUtils` visible as one of the strongest
   `creator-world foundation layer`
   donors in the repo.
2. Treat `udon-list`, `udon-dictionary`, and `udon-json` as strong
   `historical substrate`
   references rather than default modern recommendations.
3. Compare `UArrayCollections` and `VUdon-ArrayExtensions` whenever future work
   needs a sharper choice between
   `parallel-array collections` and `array extension ergonomics`.
4. Revisit `UdonUtils` when a future pass needs deeper coverage of task,
   event, or network-time subsystems.
