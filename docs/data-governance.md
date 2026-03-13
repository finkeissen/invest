# Data Governance in Invest-GT

## Purpose

This file defines the governance principles for data and input artifacts in Invest-GT.

Its purpose is to ensure that the repository's input layer remains:

- traceable
- bounded
- interpretable
- auditable
- structurally usable for downstream artifacts

In a repository like this, data governance is not a secondary operational issue.  
It is part of the epistemic structure.

If the input layer is weak, then world snapshots become weak, hypotheses drift, scenarios lose grounding, runs become harder to audit, and reports overstate what the repository can actually support.

This file is canonical for the governance of source materials, curated inputs, datasets, and snapshots.

---

## Why data governance matters here

Invest-GT does not operate on abstract symbols in a vacuum.

It works on representations of the world under uncertainty.

That means the repository depends on materials such as:

- source documents
- extracted observations
- curated notes
- datasets
- contextual bundles
- structured world-state inputs
- frozen snapshot packages for runs

Without explicit governance, these materials tend to drift into problematic states such as:

- unclear provenance
- mixed raw and interpreted content
- silently changing inputs
- unbounded scope
- hidden omissions
- broken run reproducibility
- false confidence from unstable sources

This file exists to prevent that.

---

## General principle

No input should be treated as "just data."

Every input artifact in this repository should be understood as a governed object with:

- origin
- scope
- admissibility conditions
- uncertainty characteristics
- usage constraints
- downstream consequences

The question is not merely whether input exists.

The question is whether it can responsibly support downstream repository artifacts.

---

## Relation to the broader architecture

Invest-GT is embedded in the broader Finkeissen research architecture.

That means input handling here must remain compatible with broader architectural principles such as:

- context-bound admissibility
- provenance sensitivity
- explicit stop conditions
- resistance to unbound generalization
- auditability of claims and artifact transitions

Data governance in this repository must therefore support admissibility rather than weaken it.

If an input cannot be tied to a concrete problem context or cannot be governed responsibly, it should not be silently promoted into active use.

---

## What counts as data in this repository

The term "data" is used here in a broad but structured sense.

It includes not only machine-readable datasets, but more generally all input materials that can enter the artifact pipeline.

This may include:

- raw source files
- text corpora
- manually assembled notes
- extraction outputs
- tabular datasets
- curated context bundles
- event timelines
- actor profiles
- market or macro observations
- qualitative source summaries
- structured source metadata
- frozen input packages for runs

The governance rules in this file apply to all such inputs unless explicitly exempted.

---

## Primary governance goals

The input layer should support at least the following goals.

### 1. Provenance visibility

A reviewer should be able to understand where relevant inputs came from.

### 2. Context preservation

Inputs should remain tied to the problem context for which they are being used.

### 3. Separation of raw and interpreted material

The repository should not collapse raw source material, extraction, synthesis, and conclusion into one undifferentiated layer.

### 4. Reproducibility of runs

When a run depends on an input state, that state should be recoverable or at least reconstructable.

### 5. Admissibility discipline

Not every available input should be treated as valid for active use.

### 6. Explicit uncertainty handling

Input weakness, incompleteness, conflict, or ambiguity should remain visible.

---

## Recommended data layers

The repository should eventually distinguish clearly between several input layers.

A recommended structure is:

- `data/raw/`
- `data/curated/`
- `data/canonical/`
- `data/snapshots/`
- `data/registry/`

This structure is conceptual first.  
Exact implementation may evolve, but the distinctions should remain.

---

# 1. Raw data

## Purpose

Raw data is the closest repository representation of original input material.

It should preserve the source material or source-derived material with minimal interpretive transformation.

## Typical examples

Raw data may include:

- downloaded source files
- copied source texts
- transcripts
- raw tables
- source exports
- event logs
- article collections
- source PDFs
- machine-generated extraction outputs before curation

## Governance rule

Raw data should remain clearly distinguishable from curated and canonical input artifacts.

Raw data is not yet a stable basis for downstream reasoning merely because it exists.

## Required properties

Where feasible, raw data should preserve:

- source origin
- retrieval date
- original scope
- basic format information
- relevant source metadata

## Risks if poorly governed

If raw data is poorly governed, the repository can lose:

- provenance
- interpretive boundaries
- later auditability
- reproducibility of extraction and curation steps

---

# 2. Curated data

## Purpose

Curated data is intermediate material that has been selected, cleaned, grouped, annotated, or otherwise prepared for use.

It stands between raw input and canonical pipeline-ready input.

## Typical examples

Curated data may include:

- extracted observations
- grouped source bundles
- cleaned tables
- manually annotated event lists
- filtered actor notes
- summarized input packages with retained source links

## Governance rule

Curated data should remain explicitly marked as curated.

It should not be mistaken for raw source material or for final repository conclusions.

## Required properties

Curated data should ideally include:

- references back to its raw origins
- curation date
- curation rationale
- known omissions
- transformation notes where relevant
- uncertainty or confidence notes where useful

## Risks if poorly governed

If curated data is treated as self-justifying, the repository may lose visibility into:

- how selection happened
- what was omitted
- where interpretation entered the pipeline
- whether downstream artifacts still rest on admissible support

---

# 3. Canonical data

## Purpose

Canonical data is the repository-ready input layer used to support world snapshots and related structured artifacts.

It is not merely cleaned data.  
It is governed data that has been made suitable for stable downstream use.

## Typical examples

Canonical data may include:

- registered source bundles
- structured observation packages
- actor context packages
- event and dependency bundles
- domain-specific input packages prepared for snapshot construction

## Governance rule

Canonical data should only include input artifacts that are explicit enough, traceable enough, and bounded enough for active pipeline use.

## Required properties

Canonical data should ideally include:

- stable identity
- scope statement
- time reference
- provenance references
- transformation lineage
- admissibility notes where appropriate
- known limitations

## Risks if poorly governed

If canonical data is weakly governed, downstream artifacts may appear formal while still resting on unstable or ambiguous input material.

---

# 4. Snapshots

## Purpose

Snapshots freeze a governed input state for a defined purpose.

They are one of the most important input-layer concepts in the repository because they support reproducible downstream artifact generation and execution.

## What a snapshot is

A snapshot is a bounded, versioned, identifiable representation of the relevant input state at a particular time or for a particular run context.

A snapshot is not only a file dump.  
It is a governed input package.

## Typical examples

Snapshots may support:

- world-state construction
- scenario setup
- run execution
- historical comparison
- validation against prior states

## Required properties

A snapshot should ideally include:

- snapshot ID
- creation timestamp
- scope statement
- time reference
- included input package references
- excluded or omitted area notes where relevant
- provenance bundle references
- uncertainty notes
- creation rationale
- status

## Governance rule

If a run or major artifact depends on a snapshot, that snapshot should remain recoverable or reconstructable.

Silent mutation of snapshot contents after active downstream use should not occur.

## Risks if poorly governed

Without proper snapshot discipline:

- runs become irreproducible
- reports lose auditability
- changes in inputs become invisible
- comparisons across time become misleading

---

# 5. Data registry layer

## Purpose

The input layer should also support registry-like governance.

This may include:

- dataset registry entries
- source-bundle registry entries
- snapshot registry entries
- transformation lineage references

## Governance rule

No major input artifact should depend only on folder placement for its identity and lifecycle visibility.

A governed input layer should eventually include registry support.

See also `docs/registries.md`.

---

## Recommended directory logic

A future repository structure could look like:

- `data/raw/`
- `data/curated/`
- `data/canonical/`
- `data/snapshots/`
- `data/registry/`

Within those, one may later organize by:

- domain
- geography
- problem context
- time period
- source family
- artifact family

The exact taxonomy can evolve, but the layer distinctions should remain stable.

---

## Source provenance requirements

Every materially relevant input should support provenance information appropriate to its type.

At minimum, provenance should answer:

- Where did this come from?
- When was it obtained or created?
- In what form was it obtained?
- What transformations were applied?
- What context was it collected for?

The amount of detail can vary, but provenance must remain recoverable where it matters.

---

## Recommended provenance fields

Depending on input type, useful provenance fields may include:

- `source_id`
- `source_type`
- `source_origin`
- `retrieved_at`
- `source_date`
- `author_or_originator`
- `collection_method`
- `license_or_usage_notes`
- `transformation_notes`
- `linked_raw_refs`
- `linked_curated_refs`

Not every input needs every field, but provenance should not be left implicit.

---

## Source quality and source status

The repository should not pretend all sources are equally strong.

Where relevant, inputs should support explicit notes on source quality or source status.

Useful distinctions may include:

- primary vs secondary
- raw observation vs interpretation
- official vs unofficial
- direct evidence vs indirect signal
- structured vs unstructured
- timely vs stale
- stable vs volatile
- complete vs partial

These distinctions do not automatically invalidate a source.  
They help preserve epistemic discipline.

---

## Uncertainty handling

Uncertainty in the input layer should not be hidden or deferred entirely to later stages.

Where relevant, inputs should explicitly record uncertainties such as:

- incomplete coverage
- ambiguous interpretation
- conflicting signals
- missing provenance
- temporal staleness
- extraction fragility
- source credibility limits

An uncertain input may still be usable.  
But its uncertainty should travel with it.

---

## Omission handling

What is omitted matters almost as much as what is included.

Where omission is material, input artifacts should record:

- what was deliberately excluded
- what was unavailable
- what was judged out of scope
- what remains unresolved

This is especially important for:

- snapshots
- curated bundles
- canonical context packages

Silence about omission can create false confidence.

---

## Transformation lineage

A major governance requirement is the ability to trace how input material changed as it moved through the repository.

At minimum, the repository should aim to preserve lineage such as:

- raw source → curated note
- curated bundle → canonical package
- canonical package → snapshot
- snapshot → world snapshot
- world snapshot → hypothesis or scenario

This does not require overengineering, but it does require explicit relation fields or equivalent references.

If lineage is lost, later auditability weakens significantly.

---

## Separation rules

The following separations should remain strict.

### Raw vs curated

Raw input should not be silently overwritten by curated interpretations.

### Curated vs canonical

Curated material may still be exploratory or partial.  
Canonical material is actively approved for downstream use.

### Input vs hypothesis

Input artifacts should not smuggle in claim structure without being recognized as interpretive artifacts.

### Snapshot vs current state

A snapshot is a frozen governed state.  
It is not simply "whatever currently sits in the folder."

### Source material vs report language

Source fragments and downstream narrative should remain distinguishable.

---

## Time handling

Inputs in this repository often have strong temporal properties.

A governed input layer should therefore distinguish clearly between:

- source creation date
- retrieval date
- curation date
- canonicalization date
- snapshot freeze date
- run usage date

These are not interchangeable.

Especially in geopolitical, macroeconomic, industrial, and technological contexts, temporal ambiguity can seriously weaken downstream artifacts.

---

## Data freshness and staleness

Some inputs remain relatively stable.  
Others become stale quickly.

The repository should therefore support explicit awareness of freshness where relevant.

Questions that should be answerable include:

- Is this input still current enough for the intended use?
- Is this input a historical artifact or a live context artifact?
- Was this snapshot intentionally historical?
- Has the underlying world changed enough that downstream reuse is unsafe?

Freshness is not a moral judgment.  
It is a usage property.

---

## Input admissibility

Not every available input should enter the active pipeline.

A candidate input should only move into active governed use if it is sufficiently:

- scoped
- traceable
- interpretable
- relevant to a concrete problem context
- non-deceptive in its apparent precision

An input may be excluded, held back, or marked partial if these conditions are not met.

Availability alone is not admissibility.

---

## Stop conditions at the data layer

Processing should stop or loop for revision if material input problems exist such as:

- origin is materially unclear
- scope is too vague
- transformation lineage is broken
- core uncertainty is hidden
- key omissions are unacknowledged
- temporal reference is too ambiguous
- the input package is too broad to support a defined problem context
- the input is being treated as stronger than it actually is

The correct response may be:

- further curation
- explicit downgrading of status
- narrower scope
- exclusion from active use
- snapshot rejection
- problem reformulation

Silent promotion should not be the default.

---

## Data status model

Input artifacts and datasets should ideally carry explicit status.

A useful status vocabulary may include:

- `raw`
- `curated`
- `candidate`
- `active`
- `partial`
- `stale`
- `deprecated`
- `invalidated`
- `archived`

Not every artifact needs every status, but status should remain visible where governance matters.

---

## Recommended family-specific governance

Different input families need somewhat different handling.

### Source bundles

Should emphasize:
- origin
- retrieval date
- scope
- completeness notes

### Extracted observations

Should emphasize:
- source links
- extraction method
- ambiguity notes
- contextual interpretation boundaries

### Curated tables and structured datasets

Should emphasize:
- transformation notes
- field definitions
- cleaning assumptions
- missing-value handling

### Event timelines

Should emphasize:
- time references
- source support
- event granularity
- uncertainty of sequencing

### Actor context packages

Should emphasize:
- scope
- abstraction level
- temporal validity
- omission notes

### Snapshots

Should emphasize:
- freeze date
- included refs
- excluded refs
- usage purpose
- downstream dependencies

---

## Reproducibility principle

Any downstream artifact that materially depends on input state should be reproducible at least at the level of governed references.

This does not always require perfect bit-level immutability, but it does require that the repository can answer:

- Which input package was used?
- Which snapshot was used?
- Which curated sources were in scope?
- Which transformations were already applied?

Without this, runs and reports become difficult to audit.

---

## Governance of human curation

Human intervention is not a defect in this repository.  
It is often necessary.

But human curation should be visible as curation.

Where materially relevant, curated artifacts should record:

- who curated them
- when they were curated
- what selection logic was used
- what remains uncertain
- what was excluded

Human judgment is allowed.  
Invisible human judgment is structurally dangerous.

---

## Governance of machine-assisted extraction

Machine-assisted extraction, summarization, or structuring may be useful, but it must not dissolve provenance or create false precision.

Machine-assisted input artifacts should, where relevant, record:

- that machine assistance was used
- which stage used it
- what type of transformation occurred
- what review, if any, followed
- what uncertainties remain

This is especially important when extracted material later supports hypotheses, scenarios, or reports.

---

## Governance of conflicting inputs

Conflicting inputs should not be erased merely to simplify downstream processing.

Where conflict is material, the repository should prefer one of the following:

- explicit representation of conflict
- scoped separation of conflicting claims
- source-quality-aware curation
- branching into alternative snapshot or scenario logic
- temporary hold pending clarification

The repository should avoid pretending that unresolved conflict has already been settled.

---

## Governance of sensitive compression

Some input transformations compress a large amount of source material into compact artifacts.

Examples include:

- source summaries
- actor profiles
- event bundles
- situation digests
- canonical context packages

These compressed artifacts are often useful, but they are also risky.

The more compression occurs, the more important it becomes to preserve:

- upstream references
- scope limits
- omission visibility
- uncertainty notes
- transformation lineage

Compressed clarity must not be mistaken for complete coverage.

---

## Relationship to snapshots and runs

Snapshots are the key bridge between the input layer and reproducible execution.

A run that uses inputs should ideally not point vaguely to "current data."  
It should point to:

- specific snapshot IDs
- specific canonical package references
- specific dataset or source-bundle refs where relevant

This is one of the strongest reasons to govern the data layer explicitly.

---

## Relationship to validation

Validation does not begin only after simulations or reports.

Input artifacts themselves may require validation-like checks such as:

- provenance checks
- schema checks
- completeness checks
- freshness checks
- consistency checks
- transformation review

Input-layer validation should be visible when it materially affects downstream trustworthiness.

See also `docs/contracts.md` and `docs/registries.md`.

---

## Recommended minimal metadata for governed input artifacts

Depending on artifact type, a governed input artifact should ideally support at least:

- `artifact_id`
- `artifact_type`
- `title`
- `status`
- `scope`
- `time_reference`
- `created_at`
- `updated_at`
- `source_refs`
- `lineage_refs`
- `uncertainty_notes`
- `omission_notes`

This may be extended later, but these are a useful minimum shape.

---

## Minimal review questions for input artifacts

Before an input artifact is treated as active, the following questions should be answerable:

- What is this artifact?
- What problem context is it for?
- Where did it come from?
- What transformations were applied?
- What time period does it refer to?
- What is uncertain about it?
- What was omitted?
- What downstream artifacts may depend on it?

If these questions cannot be answered, the input artifact is not governed strongly enough.

---

## Consequences for repository design

This file implies several structural directions for the repository:

- explicit distinction between raw, curated, canonical, and snapshot layers
- registry support for snapshots and datasets
- provenance-aware metadata
- transformation lineage fields
- snapshot IDs for reproducible runs
- visible handling of uncertainty, omission, and staleness

The repository does not need to implement all of this at once.  
But the architecture should assume these distinctions from the beginning.

---

## What this file does not define

This file defines data governance principles and structural expectations.

It does not yet define:

- exact schemas for datasets or snapshots
- specific file formats
- storage tooling
- automation scripts
- dataset naming conventions in final form
- detailed validation protocols for each input family

Those should be specified separately.

---

## Status of this file

This file is canonical for:

- input-layer governance
- provenance expectations
- raw/curated/canonical/snapshot separation
- uncertainty and omission handling in data artifacts
- the role of snapshots in reproducibility

Any future input-handling implementation in this repository should either:

- follow these governance principles directly, or
- document explicitly why an equivalent mechanism is being used instead
