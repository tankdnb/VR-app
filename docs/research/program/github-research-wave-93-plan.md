# GitHub Research Wave 93 Plan

- Date: `2026-04-21`
- Goal: run the next focused GitHub research wave for repositories that map
  `VRChat creator diagnostics`, `editor inspection`, `profiling`, and
  `static-analysis helpers`.

## Why this wave exists

`VR-apps-lab` had better coverage of creator runtime utilities than of
`how creators inspect, simulate, profile, or lint their worlds before they ship them`.

This wave exists to make that branch explicit.

## Search scope

Primary search directions for this wave:

- editor-side Udon or world simulators;
- Udon behaviour explorers and scene-inspection tools;
- compile-time or emit-time profiling helpers;
- analyzers or lint-like helpers for unsupported UdonSharp patterns.

## Frozen shortlist for code-level study

- `GotoFinal/GotoUdon`
- `Varneon/UdonExplorer`
- `DeltaNeverUsed/UdonSharpProfiler`
- `esnya/UdonRabbit.Analyzer`

## Secondary candidates surfaced in the same wave

These candidates were checked but not promoted into the main shortlist:

- `kibalab/CHAMCHI_Console`
  stayed outside this wave because it is closer to runtime debug UI than to
  editor or compile-time diagnostics;
- `UdonSharpRE/UdonSharpDecompiler` and `UdonSharpDisassembler`
  stayed outside this wave because this pass focused on creator diagnostics and
  feedback loops rather than reverse-engineering tools;
- `Project-Sakanah/vscode-udonsharp-linter`
  stayed outside this wave because the analyzer lineage already provided the
  stronger code-level donor surface.

## Execution model

### Step 1: Search and deduplicate

- search GitHub for Udon testing, profiling, inspection, and static analysis
  helpers;
- compare surfaced repos against `catalog/project-registry.md`;
- prefer repos where diagnostics are visible in editor windows, compiler hooks,
  or analyzer rules.

### Step 2: Freeze the shortlist

- keep the wave centered on `creator diagnostics`, not on every creator-side
  package;
- allow simulation, inspection, profiling, and static analysis to coexist when
  they clarify different feedback-loop layers.

### Step 3: Sync local source cache

- clone shortlisted repositories into `.research-sources/github/`;
- keep the clones local-only and outside git tracking.

### Step 4: Perform the code-level pass

For each shortlisted repository inspect:

- where diagnostics enter the creator workflow;
- how much of the value lives in editor UI versus code instrumentation or
  analyzer rules;
- whether the repo is strongest as an inspection tool, simulation tool, trace
  tool, or static guardrail;
- what reusable diagnostic methods belong in the methods catalog.

### Step 5: Promote findings into repository structure

Update:

- `landscape/` with a new Wave 93 synthesis document;
- `catalog/project-registry.md`;
- `landscape/project-families.md`;
- `landscape/not-yet-studied-deeply.md`;
- `methods/vr-utility-methods-catalog.md`;
- documentation indexes that surface the new wave.

### Step 6: Verify before publishing

For this type of work, the main checks are:

- editor inspection stays distinct from compile-time or static-analysis tooling;
- broad alpha repos are described honestly when coverage remains partial;
- `.research-sources/` stays ignored by git;
- the new wave is linked from the research indexes.

## Definition of done

This wave is complete when:

1. the plan and backlog are documented;
2. the shortlist is confirmed in the local source cache;
3. a Wave 93 synthesis document exists with code-level findings;
4. the registry and families represent creator diagnostics more clearly;
5. new methods are captured where this wave clarified reusable feedback-loop
   patterns;
6. documentation indexes link to the new wave;
7. the result is committed and pushed to GitHub.
