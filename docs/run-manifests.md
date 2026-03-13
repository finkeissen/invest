# Run Manifests in Invest-GT

## Purpose

This file defines the role, structure, and governance logic of run manifests in Invest-GT.

Run manifests are the canonical execution-binding artifacts of the repository.

They make explicit which governed artifacts were brought together for one concrete execution context, under which configuration, for which purpose, and with which status.

Without run manifests, a repository may still contain scenarios, hypotheses, models, results, and reports, but it becomes much harder to answer one of the most important audit questions:

> What exactly was executed?

This file is canonical for run-manifest logic.

---

## Why run manifests matter

Invest-GT is not only a documentation repository.

It is intended to support structured world modeling, explicit hypotheses, scenario construction, model use, simulation, and consequence analysis.

As soon as execution enters the picture, several structural risks appear:

- artifact versions are referenced informally
- "the scenario" is used without stable identity
- changed models silently affect output
- current configuration is mistaken for historical configuration
- results exist, but no one can reconstruct what produced them
- reports summarize runs that are not actually reproducible

Run manifests exist to prevent this.

They bind conceptual artifacts into one explicit execution context.

---

## What a run manifest is

A run manifest is a governed artifact that records one concrete execution instance or planned execution instance.

It specifies:

- what was executed
- why it was executed
- which artifacts were used
- which versions were used
- which configuration governed the run
- what status the run had
- where the outputs belong
- which downstream artifacts depend on it

A run manifest is therefore not just a log file and not just a config file.

It is the canonical reproducibility spine of a run.

---

## What a run manifest is not

A run manifest is not:

- a scenario
- a hypothesis set
- a model specification
- a snapshot
- a result artifact
- a report
- a plain runtime config without artifact references

These distinctions must remain sharp.

The manifest does not replace the underlying artifacts.  
It binds them into one explicit execution context.

---

## Core principle

A run should never depend on vague references such as:

- latest scenario
- current hypothesis set
- recent macro inputs
- active model
- today's settings
- whatever was in the folder at the time

Instead, a run should depend on explicit governed references.

A run manifest exists so that downstream reviewers can reconstruct not just the outputs, but the execution context that produced them.

---

## When a run manifest is needed

A run manifest should exist whenever a concrete execution matters enough that its context must remain reconstructable.

Typical cases include:

### 1. Simulation runs

If a scenario is executed through one or more models, a manifest should bind the exact artifact set.

### 2. Comparative runs

If two or more runs are compared, each one should have its own manifest.

### 3. Sensitivity runs

If a run explores parameter sensitivity or alternative configurations, the variants should remain manifest-visible.

### 4. Historical replay runs

If the repository replays a past condition or tests model behavior against a known situation, the exact input state and model set should be explicit.

### 5. Report-supporting runs

If a report or decision-facing output references execution results, the underlying run should be manifested.

### 6. Failed or interrupted runs that still matter analytically

A failed run may still need a manifest if the failure itself is relevant to repository learning or auditability.

---

## Planned vs executed runs

A run manifest may exist before execution, after execution, or throughout the run lifecycle.

This means a manifest may support states such as:

- planned
- executing
- completed
- failed
- cancelled

The manifest should not be understood only as a post hoc record.  
It can also be the explicit execution contract before a run begins.

---

## Run identity

Run manifests are canonical artifacts and should therefore follow stable identity rules.

Recommended ID format:

- `RUN-YYYYMMDD-###`

Examples:

- `RUN-20260312-001`
- `RUN-20260312-002`

This gives each concrete run a stable identity tied to its execution date and sequence.

If needed later, runs may also support additional version-like handling, but the main rule should remain:

one materially distinct execution context should have one distinct run identity.

See also `docs/ids-and-versioning.md`.

---

## Recommended manifest location

**Recommended directory:** `simulations/manifests/`

Possible future layout:

- `simulations/manifests/RUN-20260312-001.yaml`
- `simulations/manifests/RUN-20260312-002.yaml`

or, if runs become richer packages:

- `simulations/runs/RUN-20260312-001/manifest.yaml`

The exact storage structure can evolve.

What matters is that the manifest remains canonical and easy to reference.

---

## Run manifest as execution-binding artifact

The run manifest is the place where the repository says, concretely:

- this snapshot
- this world snapshot
- these hypotheses
- this scenario
- these agents
- these models
- this configuration
- this runtime mode
- this purpose

were bound together into one run.

This binding should be explicit enough that later artifacts do not need to guess what happened.

---

## Recommended minimum fields

Every run manifest should ideally support at least:

- `artifact_id`
- `artifact_type`
- `title`
- `status`
- `created_at`
- `created_by` where relevant
- `run_purpose`
- `problem_context`
- `snapshot_refs`
- `world_snapshot_refs` where relevant
- `hypothesis_refs`
- `scenario_ref`
- `agent_refs`
- `model_refs`
- `config_ref` or embedded config metadata
- `runtime_mode`
- `seed_info` where relevant
- `execution_notes`
- `result_refs`
- `report_refs`
- `validation_refs`
- `failure_notes`
- `tags` where useful

This set may later become a formal schema.

---

## Meaning of key run-manifest fields

### artifact_id

Stable run identity.

Example:
- `RUN-20260312-001`

### artifact_type

Should identify the artifact family clearly.

Example:
- `run_manifest`

### title

Human-readable title of the run.

Example:
- Europe energy-security allocation baseline run

### status

Current lifecycle state of the run.

Examples:
- `planned`
- `executing`
- `completed`
- `failed`
- `cancelled`

### run_purpose

The reason this run exists.

Examples:
- baseline scenario execution
- sensitivity analysis
- historical replay
- model comparison
- report support
- exploratory internal test

### problem_context

The bounded inquiry space this run addresses.

This helps avoid treating a run as universally meaningful.

### snapshot_refs

References to the frozen governed input state used by the run.

This is one of the most important fields for reproducibility.

### world_snapshot_refs

References to synthesized contextual world-state artifacts if those are distinct from input snapshots and materially used.

### hypothesis_refs

References to the explicit hypotheses that materially informed the run.

### scenario_ref

Reference to the scenario under which the run was executed.

### agent_refs

References to the agent specifications used.

### model_refs

References to the model specifications used.

### config_ref

Reference to a configuration artifact or configuration bundle that governs execution details.

### runtime_mode

The operational mode of the run.

Examples:
- deterministic
- stochastic
- replay
- perturbation
- batch comparison

### seed_info

Seed and randomness information where relevant.

This matters especially for reproducibility in stochastic settings.

### execution_notes

Notes about the run context, including non-default conditions or special caveats.

### result_refs

References to the result artifacts generated by this run.

### report_refs

References to reports that materially depend on this run.

### validation_refs

References to validation artifacts that checked the run setup or outputs.

### failure_notes

If the run failed or was partial, the failure should remain visible.

---

## Minimum binding rule

A run manifest should bind enough information to answer all of the following:

- What was this run for?
- Which input state did it use?
- Which artifact versions did it use?
- Which scenario did it instantiate?
- Which models and agents were involved?
- Which config governed execution?
- Was it deterministic or stochastic?
- Did it succeed, fail, or remain partial?
- Which results came out of it?
- Which reports later relied on it?

If these questions cannot be answered, the run is under-governed.

---

## Run status model

Runs should support a specific lifecycle status vocabulary.

Recommended statuses:

- `planned`
- `executing`
- `completed`
- `failed`
- `cancelled`
- `archived`

### planned

The run has been specified but not yet executed.

### executing

The run is currently in progress.

### completed

The run finished and produced outputs in a structurally acceptable way.

### failed

The run did not complete successfully or the execution context broke materially.

### cancelled

The run was intentionally stopped before completion.

### archived

The run is retained for history, comparison, or audit, but is not operationally current.

The exact status vocabulary may later grow, but execution state should remain explicit.

---

## Run purpose classification

A run manifest should also make clear what kind of run it is.

Useful categories may include:

- baseline
- exploratory
- sensitivity
- perturbation
- historical_replay
- scenario_comparison
- model_comparison
- validation_support
- report_support

This is helpful because not every run should be interpreted the same way.

A lightweight exploratory run should not automatically be treated like a strong report-supporting run.

---

## Run context must remain bounded

A run is never "about everything."

Even a broad run should remain context-bound.

The manifest should therefore record the intended inquiry, such as:

- stress-testing a scenario
- evaluating consequence propagation
- exploring allocation implications
- comparing rival hypotheses under one scenario
- examining sensitivity to input shifts

A run with no bounded purpose becomes difficult to interpret responsibly.

---

## Relation to snapshots

A reproducibility-sensitive run should almost always reference one or more snapshots.

This is the bridge between data governance and execution governance.

A run should not rely on floating input references when the input state matters materially.

Good:
- `snapshot_refs: [SNAP-004]`

Weak:
- uses current canonical data

Snapshot references are one of the main reasons run manifests matter.

See also `docs/snapshots.md`.

---

## Relation to world snapshots

If a run depends not only on raw or canonical inputs but also on a structured world-state synthesis, that dependency should be visible.

A run may therefore reference:

- one or more input snapshots
- one or more world snapshots

This keeps clear the difference between:
- frozen input basis
- synthesized contextual representation

Both may matter.

---

## Relation to hypotheses

A run should make visible which hypotheses materially shaped the execution context.

This matters because later reviewers may ask:

- Which claim set did this run actually instantiate?
- Did the run depend on active or draft hypotheses?
- Did the report overstate what the linked hypotheses supported?

Without explicit hypothesis refs, the conceptual basis of the run may become blurry.

---

## Relation to scenarios

A run should usually reference one primary scenario.

If the run compares multiple scenarios, that should be made explicit rather than hidden.

Possible approaches later include:

- one run per scenario
- one comparison run with multiple scenario refs
- a parent comparison package referencing multiple runs

The important point now is to keep scenario usage legible.

---

## Relation to agents and models

A run should show which operational structures were used.

This includes:

- which agent specifications were active
- which models were instantiated
- which model versions were used
- whether any special parameters or runtime overrides applied

A result without this context is hard to audit.

---

## Relation to config

A run manifest should not silently collapse into a config file, but configuration still matters.

The manifest should therefore either:

- point to a dedicated config artifact, or
- record the relevant config information directly

Examples of configuration-relevant content:

- runtime flags
- execution mode
- selected branch settings
- parameter sets
- thresholds
- output mode
- random seed handling

Configuration should remain visible enough that "same run, different settings" can be recognized as a materially different run.

---

## Relation to results

A run manifest is upstream of results.

A useful rule is:

> no result without a run reference

Results should remain attributable to specific run contexts.

The run manifest should therefore maintain explicit `result_refs` once outputs exist.

If a run fails, it may still produce partial outputs, logs, and anomaly records.  
Those should remain linked rather than disappearing into ambiguity.

---

## Relation to reports

Reports should not depend on "some run from before."

A report that materially uses execution outputs should reference the run manifest(s) behind those outputs.

This makes it possible to check whether:

- the report uses the correct run
- the report uses a completed or failed run
- the report claims more than the run supported
- the report rests on draft or active upstream artifacts

Run manifests help make this chain inspectable.

---

## Relation to validation

Runs themselves may be validation targets.

Relevant checks may include:

- completeness of references
- compatibility of artifact set
- reconstructability
- seed visibility
- run-to-result linkage
- failure visibility
- configuration clarity

A run manifest should therefore be linkable to validation records.

Useful field:
- `validation_refs`

---

## Compatibility principle

A run manifest should not merely collect references.  
It should reflect a compatible execution bundle.

The following kinds of incompatibility should be visible and blocking where material:

- scenario uses hypotheses that are rejected or invalidated
- run references models with incompatible contracts
- snapshot and world snapshot refer to mismatched scope
- run uses deprecated artifacts without explicit reason
- config contradicts the intended runtime mode

The manifest should support compatibility review, not hide incompatibility.

---

## Failure handling

A run that fails is still a meaningful governed event if the failure matters.

Failure should therefore remain explicit rather than erased.

A failed run manifest should ideally record:

- failure status
- failure point where known
- partial outputs where relevant
- whether the failure is technical, structural, or conceptual
- whether rerun is recommended
- whether downstream reporting is blocked

This is important because failed execution can still reveal weaknesses in scenarios, models, configs, or assumptions.

---

## Deterministic vs stochastic runs

The manifest should preserve whether the run was deterministic or stochastic.

### Deterministic runs

Should be reproducible from the same artifact and config state.

### Stochastic runs

Require explicit seed handling, sampling notes, or equivalent reproducibility metadata.

A manifest that hides the stochastic nature of the run weakens interpretability.

---

## Run variants and parameter sweeps

Not every run is a single one-shot execution.

The repository may later support:

- parameter sweeps
- sensitivity batches
- Monte Carlo runs
- scenario branch sweeps
- model comparison suites

Even then, run-manifest logic should remain explicit.

Possible approaches later include:

- one manifest per atomic run
- one parent manifest for the batch plus child manifests per execution
- one manifest with internal variant indexing

The implementation can evolve later.

The architectural requirement now is only that variation remains explicit and auditable.

---

## Mutability rules

### Before execution

A `planned` run manifest may still be revised.

### During execution

Changes should be controlled and visible.

### After execution

A materially completed run manifest should not be silently rewritten in a way that changes the execution history.

Allowed later edits may include:
- adding result refs
- adding report refs
- adding validation refs
- correcting obvious metadata errors without changing the actual run context

Material changes to the execution bundle should generally require a new run manifest, not silent mutation of the old one.

---

## Supersession and reruns

A rerun is usually a new run, not a new version of the same completed run.

This is especially true when:
- inputs changed
- snapshots changed
- hypotheses changed
- models changed
- config changed
- runtime mode changed

A useful practice is:

- preserve old run as its own artifact
- create new run manifest
- link them through comparison or derivation metadata where useful

Run history should remain explicit.

---

## Review questions for run manifests

Before a run manifest is treated as strong enough for active downstream use, the following questions should be answerable:

- What is this run for?
- Which exact governed artifacts does it use?
- Which snapshot state does it depend on?
- Which scenario does it instantiate?
- Which models and agents are active?
- Which config governs execution?
- Is the run deterministic or stochastic?
- What is its current status?
- Are failures or caveats visible?
- Can a reviewer reconstruct the execution context from the manifest?

If these questions cannot be answered, the run manifest is too weak.

---

## Recommended run registry

Run manifests should eventually appear in a registry, for example:

- `registry/runs.yaml`

The registry should make visible:

- run ID
- status
- purpose
- canonical manifest ref
- linked result refs
- linked report refs
- key artifact refs

See also `docs/registries.md`.

---

## Recommended future structure

A possible future structure could be:

- `simulations/manifests/RUN-20260312-001.yaml`
- `simulations/results/RES-20260312-001.yaml`
- `simulations/logs/RUN-20260312-001.log`

or, in a richer package form:

- `simulations/runs/RUN-20260312-001/manifest.yaml`
- `simulations/runs/RUN-20260312-001/results/`
- `simulations/runs/RUN-20260312-001/logs/`

The implementation can remain simple at first.

The important thing is that the manifest becomes canonical.

---

## Relationship to other canonical files

This file should be read together with:

- `docs/artifacts.md`
- `docs/ids-and-versioning.md`
- `docs/contracts.md`
- `docs/registries.md`
- `docs/data-governance.md`
- `docs/snapshots.md`
- `docs/validation-and-evaluation.md`

Those files define the artifact, identity, pipeline, registry, input, and review context within which run manifests operate.

This file specializes that logic for execution-binding artifacts.

---

## Consequences for repository design

This file implies structural additions such as:

- explicit run manifests
- result linkage by run reference
- config references as governed artifacts or controlled metadata
- run-status tracking
- run registry entries
- visible distinction between exploratory and report-supporting runs
- explicit handling of failed runs and reruns

The repository does not need to implement all of this immediately.  
But it should be designed so that runs never become opaque events.

---

## What this file does not define

This file defines the conceptual role and governance of run manifests.

It does not yet define:

- the final run-manifest schema
- exact YAML or JSON field names
- runtime orchestration tooling
- CLI interfaces
- log-storage conventions
- result schema details
- automation of manifest generation

Those should be specified separately if implementation requires them.

---

## Status of this file

This file is canonical for:

- what a run manifest is
- when it is needed
- what it must bind
- how it relates to snapshots, scenarios, hypotheses, models, results, and reports
- how it supports reproducibility and auditability

Any future execution system in this repository should either:

- follow this run-manifest logic directly, or
- document explicitly why an equivalent mechanism is being used instead
