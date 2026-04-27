# GitHub Research Wave 97 Backlog

- Date: `2026-04-27`
- Scope: next GitHub discovery wave focused on
  `Udon encoding`, `token verification`, `query helpers`, and
  `structured-data micro-libraries`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for Udon encoding, JWT, query, and XML helper
  repositories
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning archived historical helpers,
  live DSL tooling, and structured-data parsing substrate

## Work package B: Local source acquisition

- `Done` Confirm `udon-encoding` in local cache
- `Done` Confirm `udon-jwt` in local cache
- `Done` Confirm `ULinq` in local cache
- `Done` Confirm `UdonXMLParser` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect manual UTF encoding helpers in `udon-encoding`
- `Done` Inspect RS256 verification, PEM parsing, and frame-sliced modular math
  in `udon-jwt`
- `Done` Inspect source generator and Harmony compile hook strategy in `ULinq`
- `Done` Inspect `DataDictionary` and `DataList` parsing and callback flow in
  `UdonXMLParser`

## Work package D: Repository updates

- `Done` Add Wave 97 plan document
- `Done` Add Wave 97 backlog document
- `Done` Add Wave 97 synthesis document
- `Done` Update the project registry for protocol and structured-data donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new protocol, query, and parsing
  patterns
- `Done` Update documentation indexes to include Wave 97

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Keep `udon-encoding` visible as a historical constrained-runtime donor
  whenever platform-native encoding support is not enough
- `Next` Revisit `udon-jwt` when a future pass needs stronger
  `frame-sliced cryptography under Udon limits`
  comparisons
- `Next` Revisit `ULinq` whenever future creator-tooling work needs more
  `compile-hook and source-generator`
  examples
