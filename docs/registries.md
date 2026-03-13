# Registries in Invest-GT

## Purpose

This file defines the role, scope, and minimum structure of registries in Invest-GT.

Registries are the governance layer for canonical repository artifacts.

They do not replace the artifacts themselves.  
They make those artifacts findable, referencable, status-aware, and governable across time.

A repository with explicit artifacts but without registries remains partially structured.  
A repository with explicit artifacts and explicit registries becomes much easier to audit, compare, maintain, and scale.

This file is canonical for registry logic.

---

## Why registries are needed

As soon as a repository contains multiple hypotheses, scenarios, models, runs, reports, and validation records, several structural problems appear unless a registry layer exists.

Typical failure modes include:

- multiple artifacts exist, but no one knows which one is active
- artifacts can be found by file path, but not by stable identity
- superseded artifacts remain in use because status is not visible
- runs reference objects informally rather than canonically
- reports cannot be tied cleanly back to artifact histories
- validation status remains scattered across notes instead of becoming governable
- old artifacts are kept, but not distinguished from current ones

Registries exist to prevent this.

---

## What a registry is

A registry is a structured index of canonical artifacts within a defined artifact family.

A registry should answer questions such as:

- Which artifacts of this type exist?
- What is each artifact's stable ID?
- What is its current status?
- Which version is current?
- Where is the canonical artifact file or record?
- What does it depend on?
- What supersedes what?
- What is safe to use downstream?
- What is deprecated, rejected, invalidated, or archived?

A registry is therefore not just a list.  
It is a governance surface.

---

## What a registry is not

A registry is not:

- a replacement for the artifact content
- a free-form note collection
- a general wiki page
- an ungoverned directory listing
- a hidden internal implementation detail

The registry must remain inspectable and meaningful at the repository level.

---

## Registry design principle

Invest-GT should distinguish clearly between:

1. the artifact itself
2. the artifact's metadata
3. the artifact's registry presence

These are related, but not identical.

For example:

- a hypothesis file contains the actual claim structure
- the metadata inside that file identifies the artifact
- the hypothesis registry records that the artifact exists, what its current status is, and how it relates to other artifacts

This separation matters because governance requires an overview across artifacts, not only inside individual files.

---

## Registry families

The repository should eventually maintain registries for the main artifact families.

Recommended canonical registries:

- world snapshots
- hypotheses
- scenarios
- agents
- models
- runs
- results
- reports
- validation records
- datasets or source packages where relevant

Not every registry needs to be equally elaborate at the beginning, but the structure should be anticipated now.

---

## Recommended registry location

**Recommended directory:** `registry/`

This keeps governance artifacts distinct from:

- `docs/` for conceptual definitions
- `data/` for source-like materials
- `pipeline/` for process structure
- artifact family directories such as `hypotheses/`, `models/`, `scenarios/`, or `simulations/`

---

## Recommended registry files

A good initial registry layout would be:

- `registry/world-snapshots.yaml`
- `registry/hypotheses.yaml`
- `registry/scenarios.yaml`
- `registry/agents.yaml`
- `registry/models.yaml`
- `registry/runs.yaml`
- `registry/results.yaml`
- `registry/reports.yaml`
- `registry/validations.yaml`
- `registry/datasets.yaml`

This list may evolve, but these are the main canonical candidates.

---

## Why top-level registries are useful

A top-level registry layer has several advantages.

### 1. It centralizes governance

A reviewer should not need to search the entire repository to know whether `HYP-014` is active or superseded.

### 2. It supports stable references

Runs, reports, and validations can point to canonical IDs that are also registry-visible.

### 3. It supports scaling

Once artifact families grow, directory browsing alone becomes insufficient.

### 4. It supports auditability

Registries make lifecycle, supersession, and status legible across time.

### 5. It reduces hidden state

Without a registry, status often lives only in filenames, local memory, or implicit convention.

---

## Registry entry model

A registry entry should be a compact but sufficient governance record for one artifact.

The artifact file remains the richer source.  
The registry remains the canonical index.

A registry entry should not duplicate the entire artifact content.  
It should capture the minimum necessary to govern the artifact reliably.

---

## Recommended minimum fields for all registry entries

Every registry entry should ideally support at least:

- `artifact_id`
- `artifact_type`
- `title`
- `status`
- `version`
- `canonical_ref`
- `created_at`
- `updated_at`
- `created_by` where appropriate
- `supersedes` where relevant
- `superseded_by` where relevant
- `depends_on` where relevant
- `tags` where useful

These fields may be extended by family-specific needs.

---

## Meaning of core registry fields

### artifact_id

The stable identity of the artifact.

Example:
- `HYP-014`

### artifact_type

The artifact family.

Example:
- `hypothesis`
- `scenario`
- `model`

### title

A human-readable title.

The title can improve over time without replacing the artifact ID.

### status

The current governance state of the artifact.

Example:
- `draft`
- `active`
- `validated`
- `superseded`
- `rejected`

### version

The currently indexed version or revision of the artifact.

Example:
- `v2`

### canonical_ref

A path, pointer, or internal reference to the canonical artifact location.

Example:
- `hypotheses/active/HYP-014-energy-infrastructure-reallocation.md`

### created_at / updated_at

Lifecycle timestamps.

### supersedes / superseded_by

Explicit governance links when one artifact replaces another.

### depends_on

Artifact references that materially support this artifact.

Example:
- a hypothesis depending on `SNAP-004`
- a run depending on `SCN-003`, `MOD-005`, and `HYP-014@v2`

---

## Family-specific registry expectations

Different artifact families need different amounts of metadata.

The sections below describe the recommended role of each major registry.

---

# 1. World Snapshot Registry

## File
`registry/world-snapshots.yaml`

## Purpose

Tracks the available world-state artifacts that may serve as contextual bases for hypotheses, scenarios, and runs.

## Why it matters

Without a snapshot registry, it becomes difficult to know:

- which snapshot is current for a problem area
- which snapshots are archived
- which snapshots are invalidated
- what time references and scopes each snapshot covers

## Recommended additional fields

In addition to the common fields:

- `time_reference`
- `scope`
- `domain_coverage`
- `source_bundle_refs`
- `uncertainty_level` where useful

---

# 2. Hypothesis Registry

## File
`registry/hypotheses.yaml`

## Purpose

Tracks all canonical hypothesis artifacts and their governance state.

## Why it matters

The hypothesis registry is one of the most important registries in the repository.

It should make clear:

- which hypotheses are active
- which are in review
- which were rejected
- which were superseded
- which are linked to which scenarios or snapshots

## Recommended additional fields

- `claim_summary`
- `confidence_status`
- `derived_from`
- `linked_snapshot_refs`
- `linked_scenario_refs`
- `validation_refs`

---

# 3. Scenario Registry

## File
`registry/scenarios.yaml`

## Purpose

Tracks the repository's structured scenarios and their current lifecycle state.

## Why it matters

Scenarios may be reused across runs, revised over time, or archived when no longer current.

A scenario registry helps answer:

- which scenario should be used
- which scenario versions exist
- which hypotheses support the scenario
- whether the scenario is still active

## Recommended additional fields

- `time_horizon`
- `problem_context`
- `linked_hypothesis_refs`
- `linked_agent_refs`
- `linked_model_refs`

---

# 4. Agent Registry

## File
`registry/agents.yaml`

## Purpose

Tracks canonical agent specifications available for simulation or structured reasoning.

## Why it matters

Without an agent registry, the same actor may end up represented in multiple drifting forms.

The registry makes visible:

- which agent specs exist
- which are active
- which abstraction level each agent uses
- which scenarios or models rely on them

## Recommended additional fields

- `agent_type`
- `abstraction_level`
- `linked_scenario_refs`
- `linked_model_refs`

---

# 5. Model Registry

## File
`registry/models.yaml`

## Purpose

Tracks model specifications and their governance status.

## Why it matters

The model registry is central to simulation auditability.

It should make clear:

- which model is approved for what use
- whether a model is validated
- which model versions were used in which runs
- which models are deprecated or invalidated

## Recommended additional fields

- `model_purpose`
- `method_family`
- `input_contract_refs`
- `output_contract_refs`
- `validation_refs`
- `failure_mode_refs`

---

# 6. Run Registry

## File
`registry/runs.yaml`

## Purpose

Tracks all concrete execution instances.

## Why it matters

Runs are where many artifacts are bound together into one execution context.

A run registry should make visible:

- what was executed
- when it ran
- whether it completed successfully
- which artifact versions were used
- where outputs are stored

## Recommended additional fields

- `run_purpose`
- `snapshot_refs`
- `hypothesis_refs`
- `scenario_ref`
- `agent_refs`
- `model_refs`
- `config_ref`
- `execution_status`
- `result_refs`
- `report_refs`

---

# 7. Result Registry

## File
`registry/results.yaml`

## Purpose

Tracks the structured outputs of runs.

## Why it matters

Results may be compared, reviewed, flagged, invalidated, or used in reports.

A result registry helps avoid confusion between:

- raw outputs
- accepted-for-review outputs
- invalidated outputs
- archived outputs

## Recommended additional fields

- `run_ref`
- `result_type`
- `warning_refs`
- `anomaly_refs`
- `validation_refs`

---

# 8. Report Registry

## File
`registry/reports.yaml`

## Purpose

Tracks report bundles and their relation to upstream artifacts.

## Why it matters

Reports are the communication surface of the repository.

Without a registry, it becomes difficult to know:

- which report is current
- what it was based on
- whether it is still valid
- whether a report has been revised or archived

## Recommended additional fields

- `report_type`
- `run_refs`
- `result_refs`
- `validation_refs`
- `published_at` where relevant

---

# 9. Validation Registry

## File
`registry/validations.yaml`

## Purpose

Tracks validation records and the artifacts they assess.

## Why it matters

Validation should not remain scattered across comments and local notes.

The validation registry makes visible:

- what was checked
- against what criteria
- with what result
- whether unresolved issues remain

## Recommended additional fields

- `validation_type`
- `target_refs`
- `criteria_ref`
- `outcome`
- `reviewer`
- `issue_refs`

---

# 10. Dataset Registry

## File
`registry/datasets.yaml`

## Purpose

Tracks curated datasets, source bundles, or structured input packages used in the repository.

## Why it matters

The input layer is often where provenance and reproducibility first weaken.

A dataset registry helps preserve:

- source package identity
- scope and date information
- usage across snapshots and runs
- licensing or usage caveats where relevant

## Recommended additional fields

- `dataset_type`
- `source_origins`
- `time_coverage`
- `license_notes`
- `used_in_snapshot_refs`

---

## Registry granularity

Registries should remain concise enough to govern, but detailed enough to matter.

A registry entry should not attempt to reproduce the entire artifact.  
It should capture enough information to support:

- discovery
- status visibility
- dependency tracing
- lifecycle governance
- audit preparation

If a field is too detailed for the registry, it likely belongs in the artifact itself.

---

## Registry update principle

Whenever a canonical artifact is created, revised, superseded, invalidated, rejected, or archived, the relevant registry should be updated.

Registries should therefore evolve with artifact governance, not as an afterthought.

A useful rule is:

> no major artifact lifecycle change without a corresponding registry update

This helps prevent hidden state.

---

## Registry as source of governance truth

In case of ambiguity between:

- an old filename
- a stale local note
- an untracked informal reference
- a registry entry

the registry should normally be treated as the canonical governance view.

This does **not** mean the registry replaces the artifact content.  
It means the registry is the primary place to determine status and canonical identity.

---

## Relationship to file paths

Registries should not depend too heavily on folder names staying permanent forever.

A `canonical_ref` may point to a file path today, but the artifact's stable identity must remain primary.

This means:

- artifact ID is the core identity
- registry tracks where the canonical artifact currently lives
- file movement should not destroy governance continuity

---

## Registry and versioning interaction

Registries must work together with the identity and versioning logic defined in `docs/ids-and-versioning.md`.

A registry entry should make it clear:

- which artifact ID is being referenced
- which version is active or indexed
- whether newer or older versions exist
- whether the artifact was superseded, deprecated, or invalidated

Registries should not hide version transitions.

---

## Registry and stage contracts interaction

Registries are not the same as stage contracts.

- `docs/contracts.md` defines what stages may consume and produce
- registries define which artifacts exist and in what governance state

Both are needed.

A stage may be allowed to consume hypotheses in principle.  
The registry helps determine which specific hypotheses are active, valid, and available to consume.

---

## Registry and validation interaction

Registries should not claim an artifact is `validated` unless a corresponding validation record exists or is explicitly referenced.

Validation-related status changes should remain evidence-linked.

This is especially important for:

- hypotheses
- models
- results
- reports

The registry should make this connection visible.

---

## Recommended initial implementation philosophy

At the current maturity stage of the repository, registries should start simple.

A practical first version could use one YAML file per registry family with a list of entries.

This is sufficient to establish:

- canonical IDs
- current status
- canonical references
- basic dependency links

More complex indexing or automation can come later.

The important step now is to define the governance layer, not to overengineer it.

---

## Example shape of a simple registry entry

The exact schema may be defined later, but conceptually an entry might look like:

- artifact ID
- title
- version
- status
- canonical reference
- timestamps
- key dependency refs
- supersession fields

The implementation format is secondary to the governance clarity.

---

## Minimal registry checklist

For every registry family, the following questions should be answerable:

- What artifact family does this registry govern?
- Which artifacts of that family currently exist?
- What is the stable ID of each artifact?
- What is the current status of each artifact?
- Which version is current?
- Where is the canonical artifact?
- What depends on it or what does it depend on?
- What has been superseded, rejected, invalidated, or archived?

If these questions cannot be answered, the registry is too weak.

---

## Consequences for repository structure

This file implies a structural addition to the repository:

**Recommended directory:** `registry/`

This directory should be treated as the governance index layer of the repository.

It does not replace artifact directories such as:

- `hypotheses/`
- `scenarios/`
- `models/`
- `simulations/`
- `reports/`

It complements them.

---

## What this file does not define

This file defines the role and required presence of registries.

It does not yet define:

- the final YAML or JSON schemas for each registry
- automated update mechanisms
- code-level registry APIs
- validation methodology
- storage tooling
- synchronization rules between registries and artifact-local metadata

Those should be specified separately.

---

## Status of this file

This file is canonical for:

- the existence of registries as a governance layer
- the major registry families
- the role of registries in artifact lifecycle control
- the minimum governance expectations for registry entries

Any future governance system in this repository should either:

- implement this registry layer directly, or
- document explicitly why an equivalent mechanism is being used instead
