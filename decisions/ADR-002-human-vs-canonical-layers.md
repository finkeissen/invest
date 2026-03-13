# ADR-002: Separation of Human Research Layers and Canonical Repository Layers

## Status

Accepted

---

## Date

2026-03-12

---

## Context

Invest-GT is being designed as an artifact-governed, constraint-bound pipeline repository.

That architectural decision establishes that the repository's primary structure should be built around explicit artifacts, governed transitions, reproducibility, and auditable reporting.

However, a second foundational decision is required:

How should the repository treat exploratory human work that does not yet meet canonical artifact standards?

This question arises because real research work does not begin in canonical form.

It often begins as:

- rough notes
- partial interpretations
- informal sketches
- local comparisons
- temporary markdown files
- notebooks
- draft hypotheses
- ad hoc input bundles
- scratch reasoning
- early model experiments
- manual curation steps
- conversations with oneself in document form

If a repository like this tries to force all such work directly into canonical structures from the beginning, it can become rigid, slow, and artificially sterile.

But if it allows exploratory work to mingle freely with canonical artifacts, it risks:

- hidden state
- semantic drift
- broken reproducibility
- unclear status
- reports based on informal material
- implementation choices outrunning governed structure
- unreviewed assumptions leaking into active artifacts

A clear architectural decision is therefore needed on the relationship between:

- human exploratory work
- local or temporary work
- notebook or scratch workflows
- draft material
- canonical governed artifacts

---

## Decision

Invest-GT will explicitly distinguish between **human research layers** and **canonical repository layers**.

Human research layers are allowed, necessary, and expected.  
Canonical repository layers are the only layers that may serve as stable downstream dependencies for active governed artifacts, reproducible runs, and report-supporting outputs.

The core rule is:

> exploratory human work may inform the canonical layer, but it must not silently function as the canonical layer

This means:

1. rough, provisional, local, and human-centered work is legitimate
2. canonical repository artifacts must remain explicit and governed
3. promotion from human layer to canonical layer must be visible
4. downstream active artifacts should depend on canonical objects, not informal work products
5. notebooks, scratch files, and temporary notes may support research, but they are not automatically admissible repository truth

---

## Definitions

### Human research layers

Human research layers include forms of work such as:

- rough notes
- exploratory markdown documents
- working memos
- notebooks
- draft analyses
- temporary local files
- manual comparison sheets
- brainstorm material
- provisional input bundles
- local model experiments
- ad hoc scripts
- discussion fragments
- intermediate thought structures not yet stabilized as canonical artifacts

These layers are useful because they support discovery, iteration, synthesis, and conceptual experimentation.

### Canonical repository layers

Canonical repository layers include governed objects such as:

- snapshots
- world snapshots
- hypotheses
- scenarios
- agent specifications
- model specifications
- run manifests
- results
- validation records
- reports
- registries
- governed configs
- architecture decisions

These layers have explicit identity, lifecycle, and downstream meaning.

---

## Interpretation

This decision does **not** treat human exploratory work as illegitimate.

It treats it as necessary but non-equivalent to canonical artifacts.

The repository should therefore support a dual reality:

### 1. Research must remain possible

People need room to think, sketch, compare, and revise before structure becomes final.

### 2. Canonical dependency must remain governed

Once an artifact becomes part of the active repository chain, it must become explicit, identifiable, and reviewable.

The architecture should therefore not confuse:
- useful for exploration
with
- valid as a governed repository artifact

---

## Why this separation is necessary

Without a clear human-vs-canonical distinction, several predictable failure modes arise.

### Failure mode 1: hidden source of truth

The "real" logic of the repository lives in notebooks, local files, or human memory, while canonical files become decorative summaries.

### Failure mode 2: unstable downstream dependency

A scenario, run, or report quietly depends on rough notes or local state that were never formalized.

### Failure mode 3: semantic drift

Terms such as hypothesis, scenario, snapshot, or result begin meaning different things in different informal contexts without reconciliation.

### Failure mode 4: premature rigidity

Researchers avoid canonical structure because it feels too heavy for early work, so important thinking stays outside the system indefinitely.

### Failure mode 5: epistemic laundering

Rough exploratory ideas appear in downstream reports as if they had already passed through canonical governance.

This decision exists to prevent these outcomes.

---

## Core principle

Human exploratory work may be rich, useful, and insightful.

But canonical downstream use requires promotion into governed artifact form.

A useful rule is:

> exploration may influence canon; exploration is not canon until explicitly promoted

This keeps the repository flexible without making it epistemically porous.

---

## Consequences

### 1. Notebooks are allowed but secondary

Notebooks may be used for:
- exploration
- quick comparisons
- scratch model tests
- data inspection
- visualization
- early reasoning experiments

But notebooks should not be treated as the long-term primary source of canonical repository meaning.

If a notebook produces something that matters, that something should be promoted into canonical artifact form.

### 2. Rough notes are allowed but non-binding

Draft notes, early markdowns, and working memos may contain valuable reasoning.

But downstream active artifacts should not depend on them directly unless they have been promoted or formalized appropriately.

### 3. Local files are allowed but non-canonical

Local, temporary, machine-specific, or private work artifacts may exist.

But they should not be allowed to silently determine:
- active hypotheses
- active scenarios
- run meaning
- report conclusions
- canonical validation status

### 4. Promotion becomes a visible act

The transition from exploratory material to canonical artifact should be explicit.

Examples:
- rough hypothesis notes become `HYP-014`
- temporary input bundle becomes `SNAP-004`
- experimental run notes become a run manifest
- exploratory summary becomes a governed report draft

### 5. Canonical layers remain the basis of reproducibility

Reproducible runs, governed reports, and active artifact chains should point to canonical artifacts.

They should not rely on:
- unspecified notebooks
- undocumented scratch logic
- "the notes from before"
- local manual interpretations with no canonical record

---

## Promotion logic

Promotion from human layer to canonical layer should occur when a work product becomes one or more of the following:

- a meaningful downstream dependency
- a stable conceptual object
- something referenced in runs
- something referenced in reports
- something expected to persist across iterations
- something that needs lifecycle status
- something that should be reviewable by others
- something that affects reproducibility

If it matters enough to be depended on, it matters enough to be governed.

---

## What counts as promotion

Promotion is not just moving a file into another folder.

Promotion means converting a work product into a governed object with at least:

- explicit artifact type
- stable identity or canonical reference
- clear scope
- explicit relation to upstream material
- explicit status
- suitability for downstream use

The exact mechanism can vary.

But promotion must be more than aesthetic cleanup.

---

## What this decision rejects

### Rejected alternative 1: everything must be canonical immediately

This was rejected because it would create excessive friction for early-stage thinking and exploratory work.

Real research requires provisional space.

### Rejected alternative 2: notebooks and rough notes are the real repository

This was rejected because it would undermine:
- auditability
- identity stability
- lifecycle governance
- reproducibility
- artifact traceability

### Rejected alternative 3: local machine state is acceptable as operational memory

This was rejected because it creates hidden dependency, especially once runs and reports matter.

### Rejected alternative 4: informal work may silently support formal outputs

This was rejected because it invites epistemic laundering and weakens the repository's architectural discipline.

---

## Human work is not a defect

This decision intentionally avoids a false ideal of fully automated or fully formalized research.

The repository assumes that:

- humans select scope
- humans curate inputs
- humans compare interpretations
- humans judge rival hypotheses
- humans write drafts
- humans notice structural problems
- humans often create the first valuable version of an artifact informally

This is not a weakness.

The weakness would be allowing that human work to remain invisible once it becomes structurally important.

---

## Canonical work is not the same as polished work

Promotion into canonical status does not require perfect finality.

A canonical artifact may still be:

- draft
- partial
- under review
- later invalidated
- later superseded

Canonical status means governed status, not absolute certainty.

This is important because otherwise researchers may delay promotion until "fully finished," which can make the canonical layer lag too far behind reality.

---

## Allowed relations between the layers

The following relations are legitimate.

### Human layer informs canonical layer

Example:
- rough notes inform a formal hypothesis

### Human layer prepares canonical layer

Example:
- local curation work leads to a snapshot

### Human layer critiques canonical layer

Example:
- notebook exploration reveals a model weakness that leads to invalidation or revision

### Canonical layer constrains human layer

Example:
- active artifact definitions shape how new exploratory work is framed

These relations are productive and desirable.

---

## Illegitimate relations between the layers

The following relations should be treated as structurally weak or inadmissible.

### Human layer silently overrides canonical layer

Example:
- a local notebook is treated as the actual current scenario logic even though no scenario artifact was updated

### Human layer silently substitutes for canonical layer

Example:
- report conclusions depend mainly on rough notes that were never promoted

### Canonical layer is treated as decorative while real logic stays informal

Example:
- registries and manifests exist, but all meaningful choices happen elsewhere

These are anti-patterns under this ADR.

---

## Suggested directory implications

This decision suggests a visible separation in repository structure.

Possible directions include:

- `research/`
- `notebooks/`
- `scratch/`
- `notes/`

for exploratory material,

and separately:

- `data/`
- `hypotheses/`
- `scenarios/`
- `models/`
- `simulations/`
- `reports/`
- `registry/`
- `decisions/`

for governed canonical material.

The exact tree may evolve, but the distinction should remain legible.

---

## Notebooks

Notebooks deserve special treatment because they are useful but structurally risky.

### Notebooks may be used for:
- exploration
- visual inspection
- quick model experiments
- data familiarization
- rough comparative analysis

### Notebooks should not be relied on for:
- canonical artifact identity
- stable run reconstruction
- authoritative scenario definitions
- final report logic
- hidden intermediate state that later matters but is not formalized

If a notebook outcome matters, it should be promoted.

---

## Scratch notes and working memos

Scratch notes and memos are legitimate research instruments.

They are especially useful for:
- rival hypothesis comparison
- conceptual decomposition
- scope narrowing
- issue tracking
- early synthesis

But they should not silently accumulate the role of:
- hypothesis registry
- scenario registry
- report basis
- run manifest substitute

Their proper role is preparatory, exploratory, or critical.

---

## Temporary and local files

Temporary and local files are also allowed.

But the architecture should assume:

- they are non-canonical
- they may disappear
- they may be private
- they may reflect incomplete thought
- they may be machine-specific
- they may not be reviewable by others

Therefore they should not become hidden hard dependencies for active repository meaning.

---

## Human curation

Human curation is essential and fully compatible with this ADR.

But when curation becomes structurally important, it should be visible.

Examples:
- curated source bundle gets canonical identity
- selected event timeline gets snapshot linkage
- manually assembled context package becomes governed canonical data

This keeps human judgment explicit rather than invisible.

---

## Early exploratory runs

Exploratory runs are allowed.

But they should be distinguished from fully governed runs.

Possible approaches include:
- keeping them clearly marked exploratory
- using lighter-weight manifests
- prohibiting strong report use until promoted into the canonical layer

The important point is that exploratory work should not masquerade as report-grade governed output automatically.

---

## Drafts and provisional artifacts

A useful consequence of this ADR is that the canonical layer should support draft status.

That means promotion does not require fake certainty.

For example:
- a hypothesis can be canonical and still be `draft`
- a scenario can be canonical and still be `in_review`
- a report can be canonical and still be `draft`

This is preferable to keeping everything informal until the very end.

---

## Review rule for hidden dependence

A useful architectural test is:

> If this notebook, note, local file, or scratch document disappeared tomorrow, would a major active repository artifact become hard to interpret or reproduce?

If the answer is yes, then the repository likely has an improper hidden dependence and promotion should be considered.

---

## Impact on reports

Reports should be especially protected against hidden human-layer dependence.

A report should not rely materially on:
- private notes
- informal drafts
- non-promoted comparisons
- tacit analyst memory
- local notebook states

If it does, the report is under-governed even if it reads well.

---

## Impact on runs

Runs should also be protected.

A run should not depend materially on:
- local notebook-only settings
- analyst memory of what changed
- undocumented manual edits
- rough experiment files with no canonical trace

If the run matters, promotion to manifest-visible governed state is required.

---

## Impact on decisions

Architecture decisions should live in the canonical layer.

They should not remain only in:
- scattered notes
- issue fragments
- remembered conversations
- local text files

This ADR itself is part of enforcing that norm.

---

## Trade-offs

This decision has costs.

### Cost 1: more explicit promotion work

Researchers must occasionally formalize work that would otherwise stay informal.

### Cost 2: duplicated effort in the short term

Early work may exist once in rough form and once in promoted form.

### Cost 3: need for judgment about timing

Teams must decide when a work product matters enough to promote.

These costs are accepted because they prevent much larger long-term costs in:
- ambiguity
- hidden state
- irreproducibility
- report overreach
- architectural drift

---

## Review implications

Future additions to the repository should be evaluated with questions such as:

- Is this intended as exploratory work or canonical artifact?
- If exploratory, is that visible?
- If canonical, is identity and status explicit?
- Does a downstream governed object depend on something informal?
- Is promotion needed?
- Is a notebook being used as a hidden registry, manifest, or scenario definition?

These questions should become normal architectural hygiene.

---

## Relation to ADR-001

ADR-001 established that Invest-GT is an artifact-governed, constraint-bound pipeline repository.

This ADR refines that by clarifying where human exploratory work fits within that architecture.

The two decisions are complementary:

- ADR-001 says the repository is governed by explicit artifacts and constrained transitions
- ADR-002 says exploratory human work is allowed, but it must not silently replace those governed artifacts

---

## Non-goals of this decision

This decision does **not** yet define:

- exact folder names for every exploratory layer
- notebook style guides
- promotion workflow tooling
- review checklists for promotion
- local privacy rules
- collaboration tooling
- synchronization mechanisms between scratch and canonical artifacts

These may be addressed later if needed.

This ADR defines the architectural distinction, not the full operational workflow.

---

## Summary

Invest-GT will explicitly distinguish between human research layers and canonical repository layers.

This means:

- exploratory work is legitimate
- informal work is not automatically canonical
- promotion into governed artifact form must be visible
- downstream active artifacts should depend on canonical layers
- hidden dependence on notebooks, scratch files, and local notes is structurally weak

This separation is necessary to preserve both:
- real research flexibility
- real repository governance
