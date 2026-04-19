# Documentation and Navigation Refactoring Backlog

- Date: `2026-04-20`
- Goal: execute the dedicated refactor track that improves documentation
  usability, navigation clarity, and canonical role separation in
  `VR-apps-lab`.

## Status legend

- `Done`
- `In progress`
- `Next`
- `Later`

## Epic A: Public entry-point cleanup

### Goal

Make the repository easier to understand for a first-time public visitor.

### Tasks

| Status | Task | Current location | Target location or role | Notes |
|---|---|---|---|---|
| `Done` | Split root start paths into `Visitor` and `Contributor/operator` routes | `README.md` | same file, clearer sectioning | Keep public framing first; move `AGENTS.md` lower in emphasis |
| `Done` | Add dedicated refactor-track visibility to docs index | `docs/README.md` | same file | Make this refactor block discoverable without searching |
| `Later` | Mirror any important navigation refactors in Russian entry docs | `README.ru.md`, `docs/README.ru.md` | same files | Keep public bilingual entry consistent |

## Epic B: Fast recovery normalization

### Goal

Restore a true quickstart path for fresh sessions and contributors.

### Tasks

| Status | Task | Current location | Target location or role | Notes |
|---|---|---|---|---|
| `Done` | Shrink quickstart into a real `5-10 minute` recovery route | `docs/research/program/new-session-quickstart.md` | same file, shorter role | Keep only the shortest useful reading sequence |
| `Done` | Move extended operational checklist pressure out of quickstart | `docs/research/program/new-session-quickstart.md` | `docs/research/program/research-operator-quick-reference.md` | The quick reference should own the operator checklist |
| `Later` | Re-check local path and machine-specific assumptions | `docs/foundation/current-operating-context.md` | operator-facing docs if needed | Keep public context cleaner if local assumptions continue to grow |

## Epic C: Current-state layer

### Goal

Give the repo one short document for `what matters now`.

### Tasks

| Status | Task | Current location | Target location or role | Notes |
|---|---|---|---|---|
| `Done` | Create a current-state synthesis document | scattered across `current-operating-context`, `not-yet`, recent waves | `docs/research/current-focus.md` | Should summarize active families, recent waves, strong donors, and immediate next moves |
| `Done` | Link current-state doc from root and docs index | `README.md`, `docs/README.md`, `docs/research/README.md` | same files | Linked from the main English entry docs in this refactor pass |

## Epic D: Canonical data-layer normalization

### Goal

Make it obvious which file owns which kind of truth.

### Tasks

| Status | Task | Current location | Target location or role | Notes |
|---|---|---|---|---|
| `Done` | Make per-repo status ownership explicit | `docs/research/catalog/project-registry.md` | same file, stronger canonical note | `project-registry` now states that it is the source of truth for repository status |
| `Done` | Reduce independent status duplication in families | `docs/research/landscape/project-families.md` | same file, synthesis-first role | Added role note that `project-families` mirrors status for convenience only |
| `In progress` | Narrow `not-yet-studied-deeply` to queue semantics | `docs/research/landscape/not-yet-studied-deeply.md` | same file, backlog-first role | Added queue-role note and shortened immediate next-move order, but the longer family-gap section still remains |
| `Later` | Add more comparison matrices for dense families | large family docs | family-specific comparison docs if needed | Especially for high-overlap groups like overlays, OpenXR tools, and tracker bridges |

## Epic E: Archive and index rationalization

### Goal

Preserve chronology without letting archive-scale lists dominate primary entry.

### Tasks

| Status | Task | Current location | Target location or role | Notes |
|---|---|---|---|---|
| `Done` | Shorten research README reading order | `docs/research/README.md` | same file, current-entry role | Keep only the shortest useful route plus current docs |
| `Done` | Keep chronology concentrated in archive-grade indexes | `docs/research/README.md` | `docs/research/program/README.md`, `docs/research/landscape/vr-projects-master-index.md` | Research README now points to archive-grade indexes instead of carrying the full chronology |
| `Later` | Add `Recent waves` section to key indexes | `docs/research/README.md`, `docs/research/program/README.md` | same files | Make `recent` easier to scan than `all history` |

## Epic F: Dedicated refactor-track visibility

### Goal

Make this refactor block part of the canonical repository system instead of a
detached note.

### Tasks

| Status | Task | Current location | Target location or role | Notes |
|---|---|---|---|---|
| `Done` | Create dedicated documentation/navigation refactor plan | n/a | `docs/research/program/documentation-navigation-refactoring-plan.md` | This file |
| `Done` | Create dedicated documentation/navigation refactor backlog | n/a | `docs/research/program/documentation-navigation-refactoring-backlog.md` | This file |
| `Done` | Link the new refactor block from existing restructuring docs | `repository-restructuring-plan.md`, `restructuring-backlog.md` | same files | Keep alignment with broader restructuring work |
| `Done` | Link the new refactor block from folder indexes | `docs/README.md`, `docs/research/README.md`, `docs/research/program/README.md` | same files | Make the new block easy to find |

## Recommended execution order

If this refactor starts soon, the safest order is:

1. `Epic F`
   make the new block visible in existing docs.
2. `Epic B`
   fix quickstart and operator recovery pressure first.
3. `Epic C`
   add `current-focus.md` so there is a shorter current-state route.
4. `Epic D`
   reduce archive pressure in entry docs.
5. `Epic A`
   polish public entry points after the internal routes are clearer.
6. `Epic C / D / A` follow-up
   revisit `registry / families / not-yet` role boundaries once the new
   navigation layer exists.
