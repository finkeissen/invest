# Snapshots in Invest-GT

## Purpose

This file defines the role, structure, lifecycle, and governance logic of snapshots in Invest-GT.

Snapshots are one of the central reproducibility and auditability mechanisms of the repository.

They freeze a governed input state for a defined context so that downstream artifacts such as world snapshots, hypotheses, scenarios, runs, results, and reports can remain reconstructable.

Without a clear snapshot concept, the repository would be forced to rely on vague references such as:

- current data
- latest inputs
- recent context
- the state of the folder at the time
- whatever was available then

That is not sufficient for a repository that aims to support traceable, auditable, and reproducible reasoning under uncertainty.

This file is canonical for snapshot logic.

---

## Why snapshots matter

Invest-GT works with world-relevant input material that is often:

- time-sensitive
- incomplete
- curated
- revised over time
- partially interpreted
- dependent on scope choices
- unstable in its "current" form

As soon as such material supports hypotheses, scenarios, or runs, a structural problem appears:

downstream artifacts can only be audited if the input state they depended on remains recoverable.

Snapshots exist to solve that problem.

They preserve a bounded input state so that the repository can later answer questions such as:

- What exactly was in scope at the time?
- Which curated inputs were included?
- Which source packages were excluded?
- Which time reference governed the input state?
- Which run used which input state?
- Was a later change to the input layer already present at the time of the run?

Without snapshots, these questions become much harder to answer.

---

## What a snapshot is

A snapshot is a governed, bounded, identifiable freeze of relevant input state for a defined purpose.

A snapshot is not merely a copied folder and not merely a timestamp.

It is an explicit input artifact that records:

- what was included
- what was excluded
- what time reference applies
- what problem context it serves
- what lineage it has
- what downstream artifacts may use it

A snapshot should therefore be understood as a first-class artifact.

---

## What a snapshot is not

A snapshot is not:

- just the current contents of `data/`
- a generic backup
- a vague note that inputs were "recent"
- a world snapshot in the sense of a synthesized world-state artifact
- a run manifest
- a report appendix

These distinctions matter.

A snapshot belongs to the governed input layer.  
It is upstream of the world snapshot and upstream of execution.

---

## Snapshot vs world snapshot

This distinction should remain very clear.

### Snapshot

A snapshot freezes the relevant governed input state.

It answers:

> Which input materials and packages were in scope for this downstream work?

### World Snapshot

A world snapshot is a structured contextual synthesis derived from governed input material.

It answers:

> What is the relevant state of the world for this problem context?

The snapshot preserves the input basis.  
The world snapshot expresses a bounded representation derived from that basis.

A run may depend on both:
- a snapshot as frozen input base
- a world snapshot as contextual synthesis artifact

These should not be collapsed into one concept.

---

## Core snapshot principle

A downstream artifact should never depend materially on a floating reference to "the current input state."

Instead, it should depend on a defined snapshot when input stability matters.

This is especially important for:

- world-state construction
- hypothesis formation
- scenario assembly
- run execution
- report generation tied to specific historical conditions

The stronger the downstream claim, the stronger the need for snapshot discipline.

---

## When a snapshot is needed

A snapshot should be created whenever the repository needs a stable governed input state for meaningful downstream use.

Typical cases include:

### 1. Before world-state construction

If the world-state representation depends on a specific bounded set of inputs, a snapshot helps make that basis explicit.

### 2. Before major hypothesis work

If hypotheses are being derived from a curated state of the world, a snapshot prevents later drift in what those hypotheses were actually based on.

### 3. Before scenario work that depends on a specific input state

A scenario may require a fixed base state so that assumptions and pathways remain interpretable.

### 4. Before any reproducibility-sensitive run

If a run is intended to be auditable, the input state should be frozen.

### 5. Before comparative evaluation

If two runs or reports are being compared, snapshots help determine whether the comparison is valid or confounded by changed inputs.

### 6. Before publishing or archiving important outputs

If a report or major output is intended to remain interpretable over time, the underlying input state should remain reconstructable.

---

## When a new snapshot should be created

A new snapshot should usually be created when the effective governed input state changes materially.

Material changes may include:

- new source bundles entering scope
- major source removals
- changed curation logic
- changed problem scope
- changed time reference
- materially revised canonical input packages
- materially different omission set
- changed interpretation-relevant input balance

Not every editorial change requires a new snapshot.

A new snapshot is warranted when the downstream meaning of "what inputs were in force" has changed in a way that matters.

---

## When a new snapshot is not necessary

A new snapshot is usually not required for:

- spelling corrections in metadata
- filename cleanup without content change
- path refactoring while canonical refs remain stable
- non-material formatting changes
- documentation clarifications that do not alter included input state

The key question is:

> Would a downstream reviewer consider the input basis materially different?

If yes, a new snapshot is probably needed.

---

## Snapshot scope

Every snapshot must be bounded.

It should state clearly:

- what problem context it serves
- what domain scope it covers
- what temporal scope it covers
- what input layers it includes
- what is intentionally excluded

A snapshot that tries to represent "everything currently known" is too broad to be a reliable governed artifact.

The stronger pattern is:

- bounded snapshot
- explicit purpose
- explicit inclusion logic
- explicit exclusion logic

---

## Snapshot identity

Snapshots are canonical artifacts and should therefore follow the repository's identity rules.

Recommended ID format:

- `SNAP-001`
- `SNAP-002`
- `SNAP-003`

Versioning may also apply where useful, for example:

- `SNAP-003@v1`
- `SNAP-003@v2`

Whether snapshots use only new IDs for new freezes or also support versioning can be refined later.

The important point is that every snapshot has a stable identity and can be referenced unambiguously.

See also `docs/ids-and-versioning.md`.

---

## Recommended snapshot location

**Recommended directory:** `data/snapshots/`

Possible future structure:

- `data/snapshots/SNAP-001/`
- `data/snapshots/SNAP-002/`

or

- `data/snapshots/SNAP-001.yaml`
- `data/snapshots/SNAP-002.yaml`

The exact storage format may vary.

What matters is that snapshots remain explicit, identifiable, and governable.

---

## Snapshot contents

A snapshot should not be understood only as a metadata stub.

It should include enough information to make the governed input state intelligible.

A snapshot may contain or reference:

- included dataset refs
- included curated input refs
- included canonical package refs
- source bundle refs
- scope notes
- temporal notes
- omission notes
- uncertainty notes
- lineage notes
- creation rationale
- downstream usage notes

Depending on implementation, the snapshot may:
- contain references only
- contain references plus copied manifests
- bundle selected files directly
- bundle a small self-contained package

The exact approach can evolve.

---

## Recommended minimum fields for a snapshot

Every snapshot should ideally support at least:

- `artifact_id`
- `artifact_type`
- `title`
- `status`
- `version` where applicable
- `created_at`
- `created_by` where relevant
- `problem_context`
- `scope`
- `time_reference`
- `included_refs`
- `excluded_refs`
- `lineage_refs`
- `uncertainty_notes`
- `omission_notes`
- `creation_rationale`

These fields may later become part of a formal schema.

---

## Meaning of key snapshot fields

### artifact_id

Stable identity of the snapshot.

Example:
- `SNAP-004`

### problem_context

The concrete task or inquiry space for which this snapshot was created.

Example:
- Europe energy-security allocation context
- semiconductor industrial dependency modeling
- NATO escalation scenario base state

### scope

The bounded area covered by the snapshot.

This may refer to:
- geography
- domain
- actor set
- issue area
- analytical boundary

### time_reference

The relevant temporal anchor.

This is especially important in dynamic domains.

A time reference may refer to:
- a date
- a period
- a freeze window
- a historical baseline moment

### included_refs

Canonical references to the input artifacts included in the snapshot.

### excluded_refs

Canonical references to relevant materials intentionally excluded from the snapshot where such exclusion matters.

### lineage_refs

References to upstream curated or canonical artifacts from which the snapshot was assembled.

### uncertainty_notes

Visible notes about uncertainty in the input state.

### omission_notes

Visible notes about important omissions, incomplete areas, or unresolved gaps.

### creation_rationale

Why this snapshot was created and what it is meant to support.

---

## Inclusion principle

A snapshot should not include artifacts merely because they were available.

Inclusion should be governed by the problem context and scope.

A good inclusion question is:

> Does this input materially belong to the bounded state we are freezing for downstream use?

If the answer is unclear, the artifact should be:
- explicitly justified,
- deferred,
- or excluded with notation.

Availability is not enough.

---

## Exclusion principle

Exclusion should also be visible where it matters.

A snapshot should record exclusions when:

- the excluded material is relevant enough that a reviewer might reasonably expect it
- the omission changes downstream interpretation
- the exclusion is part of the bounded design

Not every non-included object needs documentation.  
But material exclusions should not remain invisible.

---

## Snapshot status model

Snapshots should support an explicit status.

Recommended statuses include:

- `draft`
- `active`
- `partial`
- `stale`
- `deprecated`
- `invalidated`
- `archived`

### draft

The snapshot is being assembled and is not ready for normal downstream dependency.

### active

The snapshot is approved for downstream use.

### partial

The snapshot is usable only with explicit caveats because coverage is knowingly incomplete.

### stale

The snapshot is historically valid as a freeze, but too outdated for certain present-focused uses.

### deprecated

The snapshot is no longer preferred because a better snapshot exists.

### invalidated

The snapshot's governance standing has broken, for example because inclusion logic, provenance, or integrity failed materially.

### archived

The snapshot is retained for history and reference but is not active.

Not every project phase needs all these statuses, but status should remain visible.

---

## Snapshot lineage

Snapshots should preserve lineage explicitly.

A reviewer should be able to see:

- from which curated packages the snapshot was assembled
- which canonical packages were included
- whether earlier snapshots were superseded
- which downstream world snapshots or runs used this snapshot

This makes snapshots part of the governed artifact graph rather than isolated files.

Useful relationship fields may include:

- `derived_from`
- `supersedes`
- `superseded_by`
- `used_by_world_snapshot_refs`
- `used_by_run_refs`

---

## Snapshot integrity

A snapshot must remain stable once active downstream artifacts depend on it.

This does not always require a heavy immutable storage system, but it does require strong governance.

The practical rule is:

> Do not silently mutate an active snapshot after it has been used downstream.

If a material change is needed, the correct response is usually:

- create a new snapshot
- supersede the old one where appropriate
- update downstream references only through explicit new artifact creation

Silent mutation destroys auditability.

---

## Snapshot mutability rules

### Before activation

A snapshot in `draft` may still be edited substantially.

### After activation

An `active` snapshot should not be materially changed in place.

Only non-material fixes may be acceptable, such as:
- typo corrections in notes
- path corrections without content change
- metadata normalization without substantive effect

### After downstream use

Once a snapshot supports:
- a world snapshot
- active hypotheses
- a scenario
- a run
- a report

material in-place changes should be considered structurally inadmissible.

A new snapshot should be created instead.

---

## Snapshot and runs

Any reproducibility-sensitive run should point to explicit snapshot refs where input state matters.

A run should ideally not say:

- uses current canonical data
- uses latest macro inputs
- uses recent geopolitical notes

A run should instead say something like:

- `snapshot_refs: [SNAP-004]`

This keeps the execution context reconstructable.

---

## Snapshot and world-state construction

A world snapshot should ideally be tied to one or more input snapshots.

This keeps clear the difference between:

- frozen governed input state
- synthesized world-state representation

A useful relation might be:

- `world_snapshot.derived_from_snapshot_refs`

This avoids false impressions that the world-state artifact emerged from nowhere.

---

## Snapshot and hypothesis formation

Hypotheses should ideally be linkable to the snapshot state under which they were formed.

This matters because hypotheses may later be reviewed against changed world conditions.

A hypothesis that looked strong under `SNAP-003` may look weak under `SNAP-007`.

Snapshot linkage helps make such shifts explicit rather than vague.

---

## Snapshot and scenario construction

Scenarios often depend heavily on a particular base state.

If the base state changes materially, the scenario may need:
- a revised scenario version
- a new scenario
- or at minimum a changed set of caveats

Snapshot linkage keeps this visible.

---

## Snapshot and reports

Reports intended to remain auditable over time should ideally reference the snapshots that grounded the artifact chain behind them.

This is especially important when reports discuss:
- historical conditions
- scenario comparisons
- run-specific interpretations
- changing world states

Without snapshot references, later readers may not know what input state the report was actually grounded in.

---

## Snapshot and validation

Snapshots themselves may require validation or review.

Relevant checks may include:

- provenance completeness
- inclusion consistency
- time-reference clarity
- omission visibility
- lineage integrity
- reproducibility of included refs

A snapshot should not automatically be treated as strong merely because it is frozen.

A frozen weak input state is still weak.

---

## Snapshot stop conditions

A snapshot should not be activated if major governance problems remain, such as:

- no clear problem context
- no clear scope
- no reliable included refs
- broken provenance in materially important components
- hidden material omissions
- ambiguous time reference
- unresolved confusion between raw, curated, and canonical inputs
- effective dependence on floating current state rather than bounded refs

In such cases, the correct response may be:

- revise the snapshot
- narrow the scope
- reduce included inputs
- mark it partial
- reject it
- keep it in draft

---

## Snapshot review questions

Before a snapshot is treated as `active`, the following questions should be answerable:

- What is this snapshot for?
- What does it include?
- What does it exclude?
- What time reference governs it?
- Which upstream artifacts did it derive from?
- What uncertainties remain?
- What omissions matter?
- What downstream artifacts may depend on it?
- Would a reviewer be able to reconstruct its effective input state?

If these questions cannot be answered, the snapshot is not governed strongly enough.

---

## Snapshot comparisons

Snapshots are also useful for comparison across time or across curation states.

Valid comparison questions may include:

- What changed between `SNAP-003` and `SNAP-007`?
- Which new input bundle entered scope?
- Did the problem scope narrow or widen?
- Did inclusion logic change?
- Was the difference material enough to affect hypotheses or runs?

This is another reason snapshots should remain explicit and versioned or superseded clearly.

---

## Snapshot supersession

When a snapshot is replaced meaningfully, supersession should be explicit.

Useful fields may include:

- `supersedes`
- `superseded_by`

This matters because not every later snapshot is simply "newer in time."  
It may be:
- broader
- narrower
- more complete
- corrected
- problem-specific

Supersession should therefore be meaningful, not automatic.

---

## Snapshot freshness and staleness

A snapshot can remain valid as a historical artifact even when it becomes stale for present-focused use.

This distinction is important.

A stale snapshot is not necessarily wrong.  
It may still be exactly the right snapshot for:

- historical replay
- comparative analysis
- validation against a prior moment
- reconstruction of an older run

The repository should not confuse:
- stale for current use
with
- invalid as an artifact

---

## Recommended snapshot registry

Snapshots should eventually appear in a registry, for example:

- `registry/world-snapshots.yaml`

or, if input-layer distinction becomes stronger later:

- `registry/snapshots.yaml`

The naming can be refined later.

The important point is that snapshots remain visible as governed canonical artifacts.

See also `docs/registries.md`.

---

## Recommended future directory pattern

A possible future structure could be:

- `data/snapshots/SNAP-001/manifest.yaml`
- `data/snapshots/SNAP-001/notes.md`
- `data/snapshots/SNAP-001/included-refs.yaml`

or a lighter version such as:

- `data/snapshots/SNAP-001.yaml`

The implementation can stay simple at first.

The architectural requirement is not complexity.  
It is explicitness.

---

## Minimal example of snapshot logic

Conceptually, a snapshot should make it possible to say:

- `SNAP-004` freezes the governed input base for Europe energy-security allocation analysis as of a defined time window
- it includes certain canonical input packages
- it excludes certain out-of-scope materials
- it carries uncertainty notes
- it supports `world snapshot WS-...`, `SCN-003`, and `RUN-20260312-001`

That is already enough to create substantial auditability improvement.

---

## Relationship to other canonical files

This file should be interpreted together with:

- `docs/artifacts.md`
- `docs/ids-and-versioning.md`
- `docs/contracts.md`
- `docs/registries.md`
- `docs/data-governance.md`

Those files define the broader artifact, identity, contract, registry, and governance context within which snapshots operate.

This file specializes that logic for snapshots specifically.

---

## What this file does not define

This file defines the role and governance of snapshots.

It does not yet define:

- a final snapshot schema
- file format choices
- automated snapshot creation tooling
- hash or immutability mechanics
- exact registry schema
- code-level snapshot APIs

Those should be defined separately if and when implementation requires them.

---

## Status of this file

This file is canonical for:

- snapshot identity
- snapshot purpose
- snapshot lifecycle
- snapshot mutability rules
- snapshot relation to runs, world-state artifacts, hypotheses, scenarios, and reports

Any future snapshot implementation in this repository should either:

- follow these rules directly, or
- document explicitly why an equivalent mechanism is being used instead
