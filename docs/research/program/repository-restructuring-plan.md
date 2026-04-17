# Repository Restructuring Plan

- Date: `2026-04-18`
- Status: `Executed in this change`
- Goal: restructure `VR.app` so it can scale from a pile of research waves into
  a maintainable system where every tracked VR repository has:
  - a place in a logical family;
  - a visible study status;
  - a path toward deeper investigation;
  - and a connection to product ideas for future VR utilities.

## Problem statement

`VR.app` had already accumulated a lot of valuable research, but it had three
structural weaknesses:

1. documents had grown in `waves`, which made chronology clearer than
   information architecture;
2. overlap between project families was understood informally, but not tracked
   systematically;
3. there was no canonical registry showing which repositories were already
   studied, only partially covered, or still waiting for a deeper pass.

That made the repository useful for historical reading, but harder to operate
as an ongoing research platform.

## Target outcomes

The restructuring had five desired outcomes:

1. `topology`
   move documents into stable folders: `foundation`, `experiments`, and
   `research`.
2. `research operating model`
   document how new repositories should be studied and recorded.
3. `canonical project tracking`
   add one place where all tracked repositories can be found by family.
4. `clear backlog`
   turn vague "we should study this later" notes into a structured backlog.
5. `navigation`
   make it easy for a new contributor to understand what to read first and how
   the research base is organized.

## Non-goals

This restructuring does **not** claim that every tracked external repository is
now fully code-audited.

What it does instead:

- makes the current knowledge base explicit;
- captures study status honestly;
- creates the scaffolding needed to deepen coverage repo by repo.

## Target information architecture

```text
docs/
  README.md

  foundation/
    README.md
    platform-foundation.md
    public-roadmap.md

  experiments/
    README.md
    reality-window/
      README.md
      overlay-vr-mvp-spec.md
      current-feasibility-status.md
      pico-official-docs-direction.md
      pico-openxr-camera-path.md
      pico-connect-constraint.md
      pico-connect-passthrough-spike.md

  research/
    README.md

    landscape/
      README.md
      vr-utilities-repo-landscape.md
      vr-projects-master-index.md
      vr-projects-wave-3-utilities.md
      vr-projects-wave-4-gap-fill.md
      vr-projects-wave-5-osc-tracking-tools.md
      vr-projects-wave-6-driver-bridges.md
      vr-projects-wave-7-depth-pass.md
      project-families.md
      not-yet-studied-deeply.md

    catalog/
      README.md
      project-registry.md

    program/
      README.md
      repository-restructuring-plan.md
      restructuring-backlog.md
      study-method.md

    reuse/
      README.md
      *.md

    templates/
      README.md
      project-study-template.md
```

## Workstreams

### Workstream 1: Documentation topology

Purpose:

- separate `stable platform docs` from `experimental findings` and `research`.

Decision:

- move platform-level docs into `docs/foundation/`
- move original reality-window feasibility work into
  `docs/experiments/reality-window/`
- move landscape and reuse docs into `docs/research/`

Result:

- completed in this change.

### Workstream 2: Canonical research operating model

Purpose:

- avoid continuing the repo as a sequence of unrelated wave documents.

Decision:

- add `program/` docs that define:
  - the restructuring plan;
  - the backlog;
  - the study method;
  - the study template.

Result:

- completed in this change.

### Workstream 3: Canonical project tracking

Purpose:

- make every tracked repository discoverable in one place.

Decision:

- add `catalog/project-registry.md` as the canonical grouped registry.

Result:

- completed in this change.

### Workstream 4: Family synthesis

Purpose:

- cluster repositories by logical overlap instead of raw chronology.

Decision:

- keep `landscape/project-families.md` as the main overlap map;
- use it to derive future product concepts and comparative studies.

Result:

- completed before and reinforced by this change.

### Workstream 5: Honest study-depth tracking

Purpose:

- stop treating "mentioned once" and "deeply analyzed" as the same kind of
  coverage.

Decision:

- use these statuses consistently:
  - `Already studied`
  - `Partially studied`
  - `Not studied deeply`
  - `Fork / variant only`

Result:

- completed in the new registry and family docs.

## Definition of done for the restructuring

The restructuring is complete when:

- all document types have a stable home;
- top-level navigation reflects the new structure;
- the repo has one visible plan and one visible backlog;
- the tracked project set is grouped into families;
- future research can be added using a standard template.

## What was completed in this change

1. moved platform, experiment, landscape, and reuse docs into structured
   subfolders;
2. added subfolder `README` files for navigation;
3. added a canonical restructuring plan;
4. added a detailed restructuring backlog;
5. added a reusable study method;
6. added a canonical project registry;
7. updated top-level documentation to point at the new structure.

## What this enables next

The repository is now ready for higher-quality follow-up work:

- family-by-family deep passes;
- comparative matrices for overlapping tool families;
- per-project deep-study documents using a stable template;
- future product selection based on study coverage instead of intuition.
