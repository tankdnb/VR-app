# GitHub Research Wave 93 Backlog

- Date: `2026-04-21`
- Scope: next GitHub discovery wave focused on
  `VRChat creator diagnostics`, `editor inspection`, `profiling`, and
  `static-analysis helpers`.

## Status legend

- `Done`
- `Next`

## Work package A: Search and shortlist

- `Done` Search GitHub for Udon simulation, inspection, profiling, and analyzer repositories
- `Done` Deduplicate the results against the registry
- `Done` Freeze a bounded shortlist spanning editor emulation, scene inspection, compiler instrumentation, and static-analysis guardrails

## Work package B: Local source acquisition

- `Done` Confirm `GotoUdon` in local cache
- `Done` Confirm `UdonExplorer` in local cache
- `Done` Confirm `UdonSharpProfiler` in local cache
- `Done` Confirm `UdonRabbit.Analyzer` in local cache
- `Done` Verify that local source cache remains outside git tracking

## Work package C: Code-level deep pass

- `Done` Inspect simulated-player runtime and debugger editor hooks in `GotoUdon`
- `Done` Inspect sortable scene inspection and metadata surfacing in `UdonExplorer`
- `Done` Inspect Harmony-based compiler instrumentation and trace output in `UdonSharpProfiler`
- `Done` Inspect analyzer rules and UdonSharp-specific diagnostics in `UdonRabbit.Analyzer`

## Work package D: Repository updates

- `Done` Add Wave 93 plan document
- `Done` Add Wave 93 backlog document
- `Done` Add Wave 93 synthesis document
- `Done` Update the project registry for creator diagnostic donors
- `Done` Update relevant overlap families
- `Done` Update `not-yet-studied-deeply.md` where follow-up themes changed
- `Done` Update the methods catalog with new diagnostics and profiling patterns
- `Done` Update documentation indexes to include Wave 93

## Work package E: Verification and publish

- `Done` Verify local source cache is still ignored
- `Done` Review git status and documentation integrity
- `Done` Verify the new wave is linked from the documentation indexes
- `Next` Commit the wave results
- `Next` Push the updated research base to GitHub

## Follow-up candidates after this wave

- `Next` Revisit `GotoUdon` when a future pass needs sharper analysis of simulation coverage boundaries and profile-launch automation
- `Next` Revisit `UdonSharpProfiler` when a future pass needs stronger trace-reading and manual instrumentation follow-up
- `Next` Compare `UdonExplorer` and `UdonRabbit.Analyzer` whenever future work needs a stronger `scene inspection plus static validation` pairing
