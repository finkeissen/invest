# ADR-004: Validation and Evaluation as First-Class Layers

## Status

Accepted

---

## Date

2026-03-12

---

## Context

Invest-GT is being designed as an artifact-governed, constraint-bound pipeline repository.

Earlier architectural decisions established that:

- the repository should be governed by explicit artifacts rather than hidden implementation state
- human exploratory work must remain distinguishable from canonical repository layers
- snapshots and run manifests form the reproducibility core for materially important work

A further architectural decision is required:

How should the repository treat validation and evaluation?

This question matters because many research and simulation repositories fail in one of two ways.

### Failure mode 1: execution is mistaken for validity

A pipeline may be able to:
- ingest inputs
- build artifacts
- run models
- produce outputs
- render reports

and yet still be weak in substantive terms because:
- hypotheses are vague
- provenance is broken
- scenarios are inconsistent
- results are fragile
- reports overstate what the upstream chain supports

In such cases, the repository works operationally but not epistemically.

### Failure mode 2: checking remains informal and non-governing

A repository may contain intelligent review comments, ad hoc critiques, and local judgment, but without a first-class validation and evaluation layer:
- checking remains scattered
- criteria remain implicit
- passing and failing are not visible states
- artifacts continue downstream despite unresolved problems
- reports reflect confidence that the system never explicitly earned

A foundational decision is therefore needed:

Should validation and evaluation be treated as secondary review activities around the real work, or as first-class architectural layers inside the repository itself?

---

## Decision

Invest-GT will treat **validation** and **evaluation** as **first-class repository layers**.

They will not be treated as optional polish, informal commentary, or downstream afterthoughts.

The core rule is:

> no artifact, run, result, or report should be treated as strong merely because it exists, executes, or reads well

This means:

1. important artifacts must be explicitly checkable
2. important checks must be recorded explicitly enough to govern progression
3. validation and evaluation outcomes must be capable of affecting artifact status and downstream use
4. structural correctness, provenance strength, admissibility, robustness, and interpretive honesty must remain visible as distinct review concerns
5. reports must not silently outrun the strength of the checked artifact chain behind them

Validation and evaluation are therefore part of the architecture itself.

---

## Interpretation

This ADR preserves a clear distinction between **validation** and **evaluation**.

### Validation

Validation asks whether an artifact, process, or output satisfies explicit checks or criteria.

Examples:
- does this hypothesis have falsification structure?
- does this run manifest reference a stable snapshot?
- does this report accurately represent validation status?
- does this model satisfy its stated contract?
- is provenance sufficiently preserved?

Validation is about explicit checkability and threshold conditions.

### Evaluation

Evaluation asks how strong, useful, robust, informative, or decision-relevant something is under stated criteria.

Examples:
- how fragile is this result under changed assumptions?
- how informative is this scenario set?
- how useful is this report for bounded allocation reasoning?
- how strong is this hypothesis relative to rivals?

Evaluation is about explicit judgment under criteria.

The repository will support both, but it will not collapse them into one vague notion of “review.”

---

## Why first-class treatment is necessary

Validation and evaluation must be first-class because otherwise they predictably lose force.

If they remain only:
- comments in documents
- remembered concerns
- notebook notes
- local conversations
- post hoc impressions

then they cannot reliably:
- block progression
- downgrade artifact status
- invalidate outputs
- restrict reporting claims
- guide comparison between alternatives

A first-class layer makes review governable rather than decorative.

---

## Consequences

### 1. Validation records become canonical artifacts

Important checks should be represented explicitly as governed artifacts or equivalent governed records.

A validation record should be able to say:
- what was checked
- how it was checked
- against which criteria
- with what outcome
- with which unresolved issues

This makes checking inspectable and reusable.

### 2. Evaluation results may affect status and permitted use

A result that is structurally valid but highly fragile may still be restricted in how it is used.

A report that is readable but interpretively overextended may be marked `in_review`, revised, or invalidated.

A hypothesis that is explicit but weak against rivals may remain active only in a limited exploratory sense.

Evaluation therefore matters architecturally, not just rhetorically.

### 3. Stage progression becomes conditional on review

Validation and evaluation must be able to stop, pause, downgrade, or qualify downstream progression.

This means the repository should allow outcomes such as:
- passed
- failed
- partial
- blocked
- strong
- adequate
- limited
- weak
- inconclusive

The exact schema may evolve, but review must have operational consequences.

### 4. Reports must remain bounded by checked support

A report may interpret results, but it must not claim more than the validated and evaluated artifact chain supports.

This means:
- uncertainty must remain visible
- weak robustness must remain visible
- incomplete validation must remain visible
- exploratory status must remain visible

Reports are downstream of review, not above it.

### 5. Validation and evaluation become distinct from implementation tests

Code tests are important, but they are not enough.

This ADR preserves the distinction between:
- technical correctness checks
- artifact validation
- substantive evaluation

A system can pass code tests and still be epistemically weak.

---

## What this decision rejects

### Rejected alternative 1: tests are enough

This was rejected because technical tests do not answer questions such as:
- is the hypothesis falsifiable?
- is the scenario coherent?
- is the report overstating certainty?
- is the run too fragile for decision-facing use?

### Rejected alternative 2: review remains informal

This was rejected because informal review is too easy to lose, forget, misinterpret, or ignore.

If review matters, it should be visible and governable.

### Rejected alternative 3: validation is only for implementation artifacts

This was rejected because non-code artifacts in this repository carry major epistemic weight.

Hypotheses, scenarios, snapshots, runs, results, and reports all require structured review.

### Rejected alternative 4: evaluation is optional if validation passes

This was rejected because a structurally valid artifact may still be too weak, too fragile, too narrow, or too misleading for the use case at hand.

Passing validation does not automatically make something strong.

---

## Review families recognized by this ADR

The repository should support multiple distinct review families, including at least the following.

### Structural validation

Checks whether artifacts are complete, well-formed, and contract-compatible.

### Provenance validation

Checks whether source lineage and transformation visibility remain sufficiently intact.

### Admissibility validation

Checks whether an artifact is context-bound and epistemically fit to remain in the active path.

### Consistency validation

Checks whether linked artifacts are mutually coherent.

### Falsification-oriented validation

Checks whether claims and hypotheses are meaningfully exposed to possible failure.

### Robustness evaluation

Checks how outputs and conclusions behave under perturbation.

### Comparative evaluation

Checks performance or usefulness relative to alternatives, baselines, or previous versions.

### Historical evaluation

Checks relation to known historical cases or historically grounded replay.

### Interpretive evaluation

Checks whether reports remain honest, bounded, and traceable in their communication.

This ADR does not require every artifact to undergo every review family, but it requires the repository to treat such distinctions as real and architecturally meaningful.

---

## Artifact families affected

This ADR applies across the repository, including at least:

- input artifacts
- snapshots
- world snapshots
- hypotheses
- scenarios
- agents
- models
- run manifests
- results
- reports
- artifact chains spanning multiple stages

Different artifact families require different review intensity, but none should be exempt merely because it is non-code.

---

## Progression rule

A strong repository must be able to say not only:
- what artifacts exist
- what was executed
- what outputs were produced

but also:
- what was checked
- what failed
- what remained unresolved
- what level of use is justified
- what level of use is not justified

This means validation and evaluation outcomes must be capable of influencing:
- status
- promotion
- report scope
- acceptable downstream dependency
- archival or invalidation decisions

If review cannot affect progression, it is structurally weak.

---

## Interaction with snapshots and run manifests

ADR-003 established snapshots and run manifests as the reproducibility core.

This ADR adds that reproducibility alone is not enough.

A reproducible weak artifact chain is still weak.

Validation and evaluation therefore sit on top of reproducibility and inspect it.

Examples:
- a snapshot may be reproducible yet provenance-limited
- a run manifest may be complete yet conceptually mismatched to the scenario
- a result may be attributable yet fragile
- a report may be traceable yet overstated

Reproducibility and review are complementary, not interchangeable.

---

## Interaction with the human-vs-canonical distinction

ADR-002 established that exploratory human work may exist outside the canonical layer.

This ADR adds that once artifacts become canonically important, their checking should also become canonical enough to govern use.

In other words:
- exploratory critique is useful
- but important critique should not remain only exploratory if it materially affects repository standing

If a notebook reveals a decisive model weakness, that insight should not remain only in the notebook.

---

## Partial acceptance and qualified use

This ADR intentionally avoids an all-or-nothing view.

Not every artifact must be either fully validated or rejected forever.

The repository should allow states such as:
- accepted with caveats
- active for exploration only
- not suitable for decision-facing reporting
- structurally valid but evaluatively weak
- partially validated pending stronger review

This matters because a strict but flexible governance model is better than either:
- loose permissiveness
- or fake binary certainty

---

## Review intensity

Not every artifact needs the same review depth.

The repository may later distinguish review intensity levels such as:
- lightweight
- standard
- high-stakes

This ADR does not fix the final review workflow, but it requires the architecture to support differential review intensity without collapsing into vagueness.

---

## Trade-offs

This decision has costs.

### Cost 1: more governance overhead

Validation and evaluation require explicit criteria, records, and maintenance.

### Cost 2: slower promotion for some artifacts

Artifacts may need to remain in draft or in review longer before downstream use.

### Cost 3: more visible uncertainty

The repository will sometimes look less “clean” because unresolved weaknesses stay visible instead of being narratively compressed.

These costs are accepted because they buy:
- stronger auditability
- more honest reporting
- better artifact discipline
- less overclaiming
- better comparison across alternatives

---

## Practical implications

This ADR implies structural directions such as:

- explicit validation records
- validation registries or registry linkage
- distinction between `tests/` and substantive review layers
- report linkage to validation and evaluation artifacts
- robustness and comparison artifacts or structured notes
- status models that can reflect review outcomes

A possible future structure may include:
- `validation/`
- `evaluation/`
- `registry/validations.yaml`

The exact implementation may evolve.

---

## Review rule

A useful architectural question is:

> Can the repository show, explicitly and inspectably, why this artifact, run, result, or report deserves the level of trust currently implied by its status and use?

If the answer is no, the validation and evaluation layer is too weak.

---

## Non-goals of this decision

This decision does **not** yet define:

- exact schemas for validation records
- exact scoring systems
- final rubric structures
- tooling for automated evaluation
- benchmark selection
- reviewer assignment workflow
- pass thresholds for every artifact family

These may be defined later.

This ADR defines the architectural role of validation and evaluation, not their final implementation detail.

---

## Relation to earlier ADRs

This ADR builds directly on:

### ADR-001

The repository is artifact-governed and constraint-bound.

### ADR-002

Exploratory human layers must remain distinct from canonical layers.

### ADR-003

Snapshots and run manifests form the reproducibility core.

ADR-004 adds that reproducibility and explicit artifacts are still not enough unless the repository also supports first-class checking and explicit judgment over those artifacts.

---

## Summary

Invest-GT will treat validation and evaluation as first-class repository layers.

This means:
- important artifacts must be explicitly checkable
- important judgments must be explicitly recordable
- review must be able to affect progression, status, and reporting
- technical execution is not enough
- readable reports are not enough
- trust must remain linked to explicit review, not inferred from polish or mere existence

This decision is foundational for making the repository not only reproducible, but also governably credible.
