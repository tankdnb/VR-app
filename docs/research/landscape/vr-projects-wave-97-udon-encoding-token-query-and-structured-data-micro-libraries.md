# VR Projects Wave 97: Udon Encoding, Token, Query, and Structured-Data Micro-Libraries

- Date: `2026-04-27`
- Goal: add the next serious GitHub discovery wave for repositories that map
  `Udon encoding`, `token verification`, `query helpers`, and
  `structured-data micro-libraries`.

## Why this wave exists

`VR-apps-lab` already had stronger coverage of broad creator utility
foundations than of:

`the narrow but very reusable helpers creators reach for when they need text encodings, frame-sliced verification, query-like ergonomics, or structured-data parsing under Udon constraints`.

This wave exists to make that branch clearer.

## Better workflow used in this wave

This wave followed the repository's post-restructure research pipeline:

1. search GitHub with Udon encoding, JWT, query, and XML helper queries;
2. deduplicate against the registry;
3. freeze a bounded shortlist;
4. inspect local source clones in `.research-sources/github/`;
5. extract methods, donor value, and family overlap;
6. promote findings into the registry, families, methods, and backlog.

## Repositories deeply studied in this wave

| Project | Why it entered the wave |
|---|---|
| `koyashiro/udon-encoding` | Strong historical donor for manual text encoding under older Udon constraints |
| `koyashiro/udon-jwt` | Strong donor for frame-sliced RS256 verification and public-key parsing under constrained runtime rules |
| `aiczk/ULinq` | Strong donor for a source-generator and compiler-hook approach to LINQ-like ergonomics in UdonSharp |
| `m-hayabusa/UdonXMLParser` | Strong donor for structured-data parsing and `DataDictionary` or `DataList` DOM-style traversal |

## Deep-pass notes by project

## `koyashiro/udon-encoding`

- GitHub:
  [koyashiro/udon-encoding](https://github.com/koyashiro/udon-encoding)
- What it is:
  an archived helper library for manual UTF-8 and UTF-32 encoding or decoding
  in UdonSharp.
- Why it matters:
  it is the clearest historical donor in this wave for
  `manual text-encoding fallback before the platform exposed a stronger native answer`.
- Interesting ideas:
  keep the API explicit through `TryGet*` methods; model encoding errors
  through helper flows rather than relying on runtime exception behavior; make
  surrogate handling visible in ordinary code.
- Interesting implementation choices:
  `Runtime/UdonUTF8.cs`
  and `Runtime/UdonUTF32.cs`
  implement manual byte or char conversion, surrogate-pair handling, and
  fallback logic directly in Udon-friendly code.
- Code donor value:
  medium-high.
- Product reference value:
  medium-high.
- Architecture reference value:
  medium.
- Caveats:
  the repository is archived and the README explicitly points creators toward
  newer native encoding support where available.
- What to inspect next:
  keep it visible whenever `VR-apps-lab` needs a
  `historical encoding workaround`
  reference.

## `koyashiro/udon-jwt`

- GitHub:
  [koyashiro/udon-jwt](https://github.com/koyashiro/udon-jwt)
- What it is:
  a creator-world helper for decoding and verifying `RS256` JWTs with PEM
  public keys.
- Why it matters:
  it is the clearest donor in this wave for
  `cryptographic verification broken into Udon-friendly chunks instead of pretending the runtime can behave like full desktop C#`.
- Interesting ideas:
  preprocess public keys into Udon-friendly arrays; validate algorithm choice
  explicitly; slice heavy modular exponentiation work across frames; expose
  progress callbacks instead of blocking the world.
- Interesting implementation choices:
  `Runtime/JwtRS256Decoder.cs`
  keeps RSA verification state in explicit fields, uses Montgomery reduction,
  and advances work through delayed-frame chunks; `PublicKeyDecoder.cs`
  parses PEM and hands off through PKCS1 or PKCS8 helpers rather than assuming
  a simpler key shape.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  very high.
- Caveats:
  this is a narrow donor and a specialized use case, not a general-purpose auth
  platform.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs stronger
  `frame-sliced cryptography`
  or
  `token verification under Udon limits`
  references.

## `aiczk/ULinq`

- GitHub:
  [aiczk/ULinq](https://github.com/aiczk/ULinq)
- What it is:
  a LINQ-like array helper for UdonSharp that uses a source generator plus a
  Harmony-based compiler hook to lower expressive source into ordinary loop
  code.
- Why it matters:
  it is the clearest donor in this wave for
  `author-friendly DSL design that disappears before UdonSharp compilation`.
- Interesting ideas:
  expose `[Inline]` methods as a source-level DSL; generate flattened loop code
  into `Library/ULinqGenerated`; intercept file reads so the compiler sees the
  transformed output rather than the ergonomic author surface.
- Interesting implementation choices:
  `SourceGenerator~/LambdaInliner.cs`
  and `ULinqGenerator.cs`
  rewrite the query surface; `Editor/ULinqCompilerHook.cs`
  patches UdonSharp file-read flow with Harmony; `Runtime/ULinq.cs`
  holds the tiny author-facing inline markers and helper entry points.
- Code donor value:
  high.
- Product reference value:
  medium.
- Architecture reference value:
  very high.
- Caveats:
  the approach is compile-pipeline invasive and best treated as a strong
  tooling donor rather than a drop-in minimal helper.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs stronger
  `creator-side compile-hook`
  or
  `DSL lowering`
  references.

## `m-hayabusa/UdonXMLParser`

- GitHub:
  [m-hayabusa/UdonXMLParser](https://github.com/m-hayabusa/UdonXMLParser)
- What it is:
  an XML parser for creator worlds that exposes parsed nodes through
  `DataDictionary` and `DataList`
  plus path-query helpers and callback-driven async parsing.
- Why it matters:
  it is the clearest donor in this wave for
  `structured-data DOM and path-query surface built on top of Udon native container types`.
- Interesting ideas:
  keep XML nodes in ordinary `DataDictionary` or `DataList` structures; expose
  path queries like `/feed/entry[0]/content`; offer async parsing through a
  callback protocol when frame cost matters.
- Interesting implementation choices:
  `Runtime/Script/XMLParser.cs`
  builds the DOM-style object model and rendering helpers; `XMLParser_Callback.cs`
  formalizes the callback surface for async parsing and result delivery.
- Code donor value:
  high.
- Product reference value:
  medium-high.
- Architecture reference value:
  high.
- Caveats:
  the async path uses a special callback object pattern and even clones its own
  GameObject, so it is not a trivial parser wrapper.
- What to inspect next:
  revisit whenever `VR-apps-lab` needs stronger
  `structured-data parsing under Udon constraints`
  references.

## Main takeaways from Wave 97

- `micro-libraries`
  are worth serious research attention because they often reveal the most
  honest constrained-runtime patterns.
- Historical donors still matter here. Even when native support improved,
  archived repos like `udon-encoding`
  still show useful fallback shapes and error-handling strategies.
- The strongest lesson from this wave is that creator tooling does not stop at
  runtime helpers:
  `ULinq`
  shows how much leverage can come from compile-time authoring ergonomics.
- Structured data in Udon worlds can be much richer than flat strings if
  creators lean on `DataDictionary` and `DataList`
  intentionally.

## Reusable methods clarified by this wave

- `Manual encoding fallback layer for constrained Udon runtimes`
- `Frame-sliced JWT verifier with predecoded key material and progress callbacks`
- `Source-generator plus Harmony compile-hook DSL that lowers into plain loops for UdonSharp`
- `Structured-data parser over DataDictionary or DataList with async callback parsing and path queries`

## Recommended next moves after this wave

1. Keep `udon-jwt` visible as one of the strongest
   `constrained cryptography`
   donors in the repo.
2. Treat `udon-encoding` as a strong
   `historical fallback`
   reference rather than a default modern recommendation.
3. Revisit `ULinq` whenever future creator-tooling work needs sharper
   `compile-hook and authoring-surface`
   comparisons.
4. Revisit `UdonXMLParser` whenever `VR-apps-lab` needs stronger
   `structured data and path-query`
   donors for creator worlds.
