# Study Method

- Date: `2026-04-18`
- Goal: define a consistent way to study a VR-related repository and extract
  useful implementation knowledge for `VR.app`.

## Core principle

Do not stop at "what the project is".

For every repository, we want to understand:

1. what user problem it solves;
2. what technical pattern it uses;
3. what parts are reusable;
4. what product ideas it unlocks for `VR.app`;
5. what still needs deeper inspection.

## Required fields for every project study

Every meaningful project note should eventually capture:

- `what it is`
- `why it matters`
- `interesting ideas`
- `interesting implementation choices`
- `code donor value`
- `product reference value`
- `architecture reference value`
- `caveats / licensing / risks`
- `what to inspect next`

## Study depth levels

### Level 0: Mentioned

- repository is known and placed in a family;
- no meaningful technical extraction yet.

### Level 1: Landscape note

- README-level understanding is captured;
- product value and likely family are identified.

### Level 2: Deep pass

- repository structure has been inspected;
- important modules and internal boundaries are identified;
- stronger implementation notes are documented.

### Level 3: Donor extraction

- concrete reusable patterns are extracted for `VR.app`;
- integration risks and licensing constraints are clearly written.

### Level 4: Prototype influence

- ideas from the repo directly inform a `VR.app` module, prototype, or code
  experiment.

## Recommended study flow

### Step 1: Intake

- record repository URL;
- place it in a `family`;
- assign a current `study status`.

### Step 2: README and metadata pass

- understand scope;
- identify whether it is:
  - `code donor`
  - `architecture reference`
  - `product reference`
  - `research only`

### Step 3: Repository structure pass

- inspect top-level folders;
- identify app/driver/service/plugin splits;
- note packaging, install flow, and runtime assumptions.

### Step 4: Technical extraction

Look for:

- overlay lifecycle patterns;
- runtime/layer registration flow;
- driver/service boundaries;
- settings storage model;
- input routing;
- device model abstractions;
- capture/rendering/compositor model;
- IPC, OSC, WebSocket, or BLE patterns.

### Step 5: Product extraction

Ask:

- what is the smallest user-visible feature here?
- is this a micro-utility, dashboard, service, or framework?
- could this become a `VR.app` module?

### Step 6: Registry update

Update:

- `catalog/project-registry.md`
- `landscape/project-families.md`
- `landscape/not-yet-studied-deeply.md` when relevant

### Step 7: Follow-up decision

Choose one:

- no more action needed;
- needs a deeper code pass;
- deserves a comparative matrix entry;
- should influence a future product backlog item.

## What counts as "interesting solution"

Interesting solutions are not only algorithms.

They also include:

- clean packaging or install flow;
- strong interaction metaphors;
- useful config models;
- smart background-service design;
- practical runtime/layer management UX;
- minimal but high-value utilities.

## What to avoid

- do not duplicate the repository README without adding interpretation;
- do not mix "mentioned" and "deeply studied" as if they were the same;
- do not add a repo to `VR.app` without updating family placement and study
  status;
- do not treat forks as first-class priorities before understanding the
  upstream family.
