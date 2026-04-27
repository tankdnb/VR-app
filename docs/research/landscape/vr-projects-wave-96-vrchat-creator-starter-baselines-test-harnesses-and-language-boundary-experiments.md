# VR Projects Wave 96: VRChat Creator Starter Baselines, Test Harnesses, and Language-Boundary Experiments

- Date: `2026-04-27`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `VRChat creator starter baselines`, `test harnesses`, and
  `language-boundary experiments`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage of creator-world runtime systems
than of:

`how creator projects are bootstrapped, how small Udon units are validated, and how far creators can push alternative-language pipelines before they land as ordinary UdonSharp`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with VRChat template, Udon test, and UdonSharp codegen
   queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `vrchat-community/template-world` | Strong donor for official bootstrap and package-restoration flow in current creator-world baselines |
| `vrchat-community/template-udonsharp` | Useful historical variant that clarifies how official template lineage converged |
| `koyashiro/udon-test` | Strong donor for an in-world assertion and test helper surface for UdonSharp |
| `raii-x/wasm2usharp` | Strong donor for unusual language-boundary code generation that still lands in ordinary UdonSharp output |

## Deep-pass notes by project

## `vrchat-community/template-world`

- GitHub:
  [vrchat-community/template-world](https://github.com/vrchat-community/template-world)
- What it is:
  the official current starter template for VRChat world projects.
- Why it matters:
  it is the clearest donor in this wave for
  `project bootstrap that restores the right creator-world package substrate on editor open instead of assuming the project is already healthy`.
- Interesting ideas:
  keep the template lightweight; fetch current package bootstrap information
  from VRChat config at editor load; restore the resolver automatically when the
  expected package is missing.
- Interesting implementation choices:
  `Packages/com.vrchat.core.bootstrap/Editor/Bootstrap.cs`
  checks whether the VPM resolver is present, queries VRChat config,
  regex-extracts the resolver package URL, downloads the unitypackage into
  temp storage, and imports it automatically through the editor.
- Code donor value:
  high.
- Product reference value:
  very high.
- Architecture reference value:
  high.
- Caveats:
  this is mostly a bootstrap donor rather than a broad runtime-system donor.
- What to inspect next:
  revisit when `VR-apps-lab` needs a stronger
  `official creator bootstrap`
  reference.

## `vrchat-community/template-udonsharp`

- GitHub:
  [vrchat-community/template-udonsharp](https://github.com/vrchat-community/template-udonsharp)
- What it is:
  a deprecated official template whose strongest current value is showing the
  migration from a dedicated UdonSharp template to the unified world template.
- Why it matters:
  it is the clearest historical variant in this wave for
  `official template convergence`
  rather than for new runtime ideas.
- Interesting ideas:
  keep the same bootstrap flow across official templates so migration is mostly
  about packaging and project framing rather than a new initialization model.
- Interesting implementation choices:
  it shares the same
  `Packages/com.vrchat.core.bootstrap/Editor/Bootstrap.cs`
  bootstrap strategy as `template-world`, which makes its strongest value
  lineage and migration context rather than new implementation surface.
- Code donor value:
  medium.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  it is deprecated and no longer the mainline recommendation.
- What to inspect next:
  keep it visible only as a
  `historical template variant`
  and migration reference.

## `koyashiro/udon-test`

- GitHub:
  [koyashiro/udon-test](https://github.com/koyashiro/udon-test)
- What it is:
  a small UdonSharp test helper that exposes assertions for creator-world code.
- Why it matters:
  it is the clearest donor in this wave for
  `in-world assertion-based testing under Udon constraints`.
- Interesting ideas:
  keep the public surface tiny; make assertions work over simple values and
  Udon data containers; format clear pass or fail output instead of inventing a
  heavy test runner.
- Interesting implementation choices:
  `Packages/net.koyashiro.udontest/Runtime/Assert.cs`
  implements recursive equality over arrays, `DataToken`, `DataList`, and
  `DataDictionary`; formats green or red rich-text output; and exposes minimal
  `Equal`, `True`, `False`, and `Null`
  checks as the author-facing API.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium-high.
- Caveats:
  it is intentionally small and does not try to model a full test framework.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs a stronger
  `creator-world unit-test substrate`
  reference.

## `raii-x/wasm2usharp`

- GitHub:
  [raii-x/wasm2usharp](https://github.com/raii-x/wasm2usharp)
- What it is:
  a Rust tool that validates WebAssembly modules, lowers them into its own IR,
  and generates UdonSharp code that can execute the translated logic.
- Why it matters:
  it is the clearest donor in this wave for
  `non-C# authoring that still lands as ordinary UdonSharp output with an explicit generated runtime substrate`.
- Interesting ideas:
  validate Wasm features before translation; run cleanup and optimization passes
  over a custom IR; generate UdonSharp fields and methods for exports, imports,
  memory, globals, and stack storage; support a plain C# test mode so the
  generated output can be inspected outside Udon.
- Interesting implementation choices:
  `src/lib.rs`
  wires CLI and validation; `src/codegen/module.rs`
  builds the generated UdonSharp class surface; `examples/Assets/ExecuteHello.cs`
  shows the explicit runtime handshake through `w2us_init()`, memory writes,
  and exported function calls.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  very high.
- Caveats:
  it is an advanced experiment rather than a mainstream creator workflow.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs stronger
  `language-boundary` or
  `codegen-to-UdonSharp`
  comparisons.

## Main takeaways from Wave 96

- `creator bootstrap substrate`
  is a real donor branch of its own, not just boring setup glue.
- The official VRChat template lineage now looks clearer:
  `template-world`
  is the current baseline, while `template-udonsharp`
  is mostly a historical migration node.
- Creator-world testing does not need a massive framework to be useful;
  a small assertion surface with honest data-container support already teaches a
  lot.
- The most surprising lesson from this wave is that
  `UdonSharp`
  can also act as a generated target language, not only as the hand-authored
  surface.

## Reusable methods clarified by this wave

- `Self-restoring creator bootstrap on editor open through remote config and package import`
- `In-world assertion library with recursive equality over arrays and Udon data containers`
- `Language-boundary code generation from Wasm into an explicit UdonSharp runtime substrate`

## Recommended next moves after this wave

1. Keep `template-world` visible as the strongest
   `official creator bootstrap`
   donor currently in the repo.
2. Treat `template-udonsharp` as a
   `variant and migration reference`
   rather than as a fresh mainline donor.
3. Revisit `udon-test` whenever future creator diagnostics work needs a clearer
   `small testing substrate`
   comparison line.
4. Revisit `wasm2usharp` whenever a future pass needs stronger
   `alternative-language to creator-world runtime`
   architecture references.
