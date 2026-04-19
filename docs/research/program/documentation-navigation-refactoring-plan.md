# Documentation and Navigation Refactoring Plan

- Date: `2026-04-20`
- Status: `Active refactor block`
- Goal: keep `VR-apps-lab` usable as a public `knowledge repository`,
  `pattern library`, and `working lab` even as the research corpus grows.

## Why this refactor block exists

The repository is already strong in content, but its documentation system is
starting to show `information-architecture` pressure:

1. `canonical status duplication`
   project status and next-step meaning now appear across `project-registry`,
   `project-families`, and `not-yet-studied-deeply`.
2. `entry-point overload`
   quickstart and reading-order docs are becoming too large for true
   session recovery.
3. `public/operator mixing`
   some public-facing entry points still blend visitor guidance with
   assistant/operator workflow.
4. `archive pressure`
   `program/` and `landscape/` indexes increasingly act like chronological
   archives instead of current working maps.
5. `missing current-state layer`
   the repository has history and backlog, but no short central document for
   `what matters now`.

## Refactor principles

This block should follow five rules:

1. `preserve history`
   do not throw away wave history; move it behind calmer entry points.
2. `one source of truth per concern`
   each document should have one clear job.
3. `separate audience layers`
   distinguish `public visitor`, `active contributor`, and `operator/session`
   needs.
4. `optimize for 5-10 minute recovery`
   a fresh session should be able to regain useful context quickly.
5. `prefer role changes over random rewrites`
   first clarify what each file is for, then simplify or move content.

## Core diagnosis

### 1. Public entry points are conceptually right, but still too dense

`README.md` and `docs/README.md` already frame the repo correctly as
`foundation + research`, but they still point users toward very large operator
documents too early.

### 2. Research entry is too chronology-heavy

`docs/research/README.md` now contains an exhaustive reading-order chain that
is useful as an archive, but too heavy as a primary navigation document.

### 3. Canonical research documents are doing multiple jobs

The following files are all valuable, but their roles are overlapping:

- `catalog/project-registry.md`
- `landscape/project-families.md`
- `landscape/not-yet-studied-deeply.md`
- `methods/vr-utility-methods-catalog.md`

The repo now needs a sharper division between:

- `source of truth`
- `synthesis`
- `priority queue`
- `method extraction`

### 4. Current-state visibility is weak

A new visitor or new session can discover the entire history, but cannot as
quickly discover:

- what the strongest families are now;
- what the most active backlog directions are;
- which docs are archival versus current;
- which 3-5 waves matter most as recent reference points.

## Target document roles

### Root and public entry

- `README.md`
  public-facing repository framing, short start paths, and high-level map only.
- `docs/README.md`
  concise documentation hub with stable routes into `foundation`,
  `research`, and active refactor tracks.

### Operator and session recovery

- `docs/foundation/current-operating-context.md`
  snapshot of current repository state, direction, and constraints.
- `docs/research/program/new-session-quickstart.md`
  short recovery route for a fresh session, not a long reading curriculum.
- `docs/research/program/research-operator-quick-reference.md`
  one-screen execution checklist.
- `AGENTS.md`
  assistant/operator rules, not the primary public entry.

### Canonical research system

- `docs/research/catalog/project-registry.md`
  single source of truth for per-repository status and in-scope tracking.
- `docs/research/landscape/project-families.md`
  synthesis, overlap, comparison, and family-level product directions.
- `docs/research/landscape/not-yet-studied-deeply.md`
  active deep-study queue and follow-up priorities only.
- `docs/research/methods/vr-utility-methods-catalog.md`
  reusable method extraction only.

### Archive and chronology

- `docs/research/program/README.md`
  program-layer map and chronological wave-plan inventory.
- `docs/research/landscape/README.md`
  landscape-layer map and synthesis-doc inventory.
- `docs/research/landscape/vr-projects-master-index.md`
  archive-grade cross-wave reference index.

## Target additions

### 1. `docs/research/current-focus.md`

Keep one short `current focus` document that extracts:

- strongest current families;
- top-priority follow-up directions;
- latest completed waves;
- strongest donor clusters;
- immediate repo-maintenance priorities.

This document should become the first stop after `current-operating-context.md`
for anyone who needs `what matters now`.

### 2. Optional `docs/contributing/` or operator-only layer later

If the public/operator split keeps growing, consider a later dedicated layer
for contributor and operator material. This is not required immediately, but it
is a likely future direction.

## Proposed move and role-change map

| Current file or section | Current problem | Proposed target role or location | Planned change |
|---|---|---|---|
| `README.md` `Start here` | mixes public orientation with operator-first routes | keep in `README.md`, but split into `Visitor path` and `Contributor/operator path` | do not remove links, but reorder and reduce operator-first emphasis |
| `docs/README.md` | strong index, but no visible active refactor track | keep as stable docs hub | add dedicated refactor-track links and current-state entry |
| `docs/research/README.md` long reading order | behaves like an archive more than an entry doc | keep as research-system hub | trim recommended reading to current route; move exhaustive chronology burden to `program/README.md` and `vr-projects-master-index.md` |
| `docs/research/program/new-session-quickstart.md` | recovery path is longer than a real quickstart should be | keep in place | compress to a 5-10 minute recovery route |
| `docs/research/program/research-operator-quick-reference.md` | currently useful, but not yet the main operator screen | keep in place | absorb extended checklist material from quickstart where appropriate |
| `docs/foundation/current-operating-context.md` local path assumptions | partly mixes public context with local-machine recovery hints | keep public context here; move machine-specific operator hints elsewhere if they grow | slim if needed after quickstart refactor |
| `docs/research/catalog/project-registry.md` | already claims canonical status, but that role is not enforced strongly enough elsewhere | keep as canonical source | explicitly make it the source of truth for per-repo status |
| `docs/research/landscape/project-families.md` | family synthesis is mixed with status repetition | keep as synthesis/comparison doc | reduce independent status ownership; keep family insight primary |
| `docs/research/landscape/not-yet-studied-deeply.md` | mixes queue, family gaps, and broad current-state summary | keep as active queue | narrow to follow-up backlog and shorter next-move section |
| `docs/research/README.md` exhaustive chronology | duplicates archive-style navigation | shift archive pressure to `program/README.md` and `vr-projects-master-index.md` | keep short current route in `research/README.md` |
| wave chronology across multiple READMEs | currently spread across several large files | archive role should live mainly in `program/README.md` and `vr-projects-master-index.md` | avoid making every README carry full historical load |

## Refactor blocks

### Block A: Public entry-point cleanup

Purpose:

- make the repository legible for a first-time visitor;
- reduce operator-specific noise in the first screenful.

### Block B: Fast recovery normalization

Purpose:

- make fresh-session recovery truly fast again;
- keep deep reading optional instead of mandatory.

### Block C: Canonical data-layer normalization

Purpose:

- remove ambiguity about where status, family, queue, and method truth lives.

### Block D: Archive and index rationalization

Purpose:

- preserve history without forcing every user through archive-scale documents.

### Block E: Current-state layer

Purpose:

- add one short place to answer `what matters now`.

## Success criteria

This refactor block should be considered successful when:

1. a new visitor can understand the repo in under `5` minutes;
2. a new session can recover enough context in under `10` minutes;
3. project status has one obvious canonical owner;
4. families, backlog, and methods no longer compete for the same role;
5. archive-scale history stays available without overwhelming the main route.

## Relationship to existing restructuring docs

This plan does not replace:

- `repository-restructuring-plan.md`
- `restructuring-backlog.md`

Instead, it narrows one active restructuring problem:

- `documentation usability`
- `navigation scale`
- `canonical role clarity`

The detailed execution tasks for this block live in:

- `documentation-navigation-refactoring-backlog.md`
