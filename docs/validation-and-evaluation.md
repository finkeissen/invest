# Validation and Evaluation in Invest-GT

## Purpose

This file defines the role, boundaries, and structure of validation and evaluation in Invest-GT.

Its purpose is to ensure that artifacts, simulations, and reports are not treated as trustworthy merely because they are well-formed, plausible, or operationally executable.

In this repository:

- validation asks whether something holds up under explicit checks
- evaluation asks how useful, strong, robust, or decision-relevant something is under explicit criteria

Both are necessary.  
Neither should remain vague.

This file is canonical for the repository's validation and evaluation logic.

---

## Why this matters

A repository like Invest-GT can fail in two opposite ways.

### Failure mode 1: technical formalism without real checking

Artifacts may be cleanly structured, versioned, and executable, yet still rest on weak assumptions, unstable inputs, or untested logic.

### Failure mode 2: vague substantive judgment without explicit criteria

People may say things like:

- this looks convincing
- the model seems reasonable
- the scenario feels plausible
- the output is probably good enough

without documenting what was checked or why that judgment should carry weight.

This file exists to prevent both failures.

---

## General principle

No major artifact or output should be treated as strong merely because it exists.

It should be possible to say, explicitly:

- what was checked
- how it was checked
- against which criteria
- with what outcome
- with which unresolved issues
- for what use case the result is good enough, if any

Validation and evaluation are therefore not decorative review layers.  
They are core governance mechanisms.

---

## Relation to the broader architecture

Invest-GT is embedded in the broader Finkeissen research architecture.

That means validation and evaluation here must remain compatible with broader architectural principles such as:

- admissibility before promotion
- context binding
- provenance sensitivity
- explicit stop conditions
- traceable artifact transitions
- resistance to hallucinated or unbound claims

Validation and evaluation should therefore not be used to cosmetically justify artifacts that are already epistemically weak.

They should be used to make strength and weakness explicit.

---

## Validation vs evaluation

These two terms should remain clearly distinguished.

### Validation

Validation asks whether an artifact, process, or output satisfies explicit checks or criteria.

Examples:

- Does this artifact conform to its schema?
- Is provenance sufficiently intact?
- Does the run manifest reference all required inputs?
- Is the hypothesis meaningfully falsifiable?
- Does the model satisfy its stated input/output contract?
- Did the run complete under reconstructable conditions?

Validation is about explicit checkability.

### Evaluation

Evaluation asks how strong, useful, robust, interpretable, or decision-relevant an artifact or output is for a given purpose.

Examples:

- How informative is this scenario set?
- How robust is the conclusion under changed assumptions?
- How decision-relevant is this report?
- How much explanatory value does this hypothesis actually provide?
- How sensitive is the result to specific model choices?

Evaluation is about explicit judgment under criteria.

Validation and evaluation overlap, but they are not the same.

---

## Why the distinction matters

An artifact may be:

- validly formed but not very useful
- operationally executable but substantively weak
- interesting but insufficiently validated
- technically clean but fragile under perturbation
- strongly argued but still provenance-limited

Without separating validation from evaluation, these distinctions are often lost.

That leads to inflated confidence.

---

## Core principle

A valid artifact is not automatically a strong artifact.  
A strong artifact is not automatically a final artifact.  
A useful artifact is not automatically an admissible artifact.

This repository must preserve those distinctions.

---

## Main validation and evaluation targets

The repository should eventually support validation and evaluation across at least the following targets:

- input artifacts
- world snapshots
- hypotheses
- scenarios
- agent specifications
- model specifications
- run manifests
- execution outputs
- result artifacts
- report bundles
- artifact chains across multiple stages

Different targets require different checks.

---

## Main validation and evaluation families

A practical structure for this repository is to distinguish several major families of checking.

### 1. Structural validation

Checks whether an artifact is complete, well-formed, and contract-compatible.

### 2. Provenance validation

Checks whether origin, lineage, and source support are sufficiently preserved.

### 3. Admissibility validation

Checks whether the artifact satisfies the epistemic and contextual constraints required for active repository use.

### 4. Consistency validation

Checks whether the artifact is internally coherent and compatible with related artifacts.

### 5. Falsification-oriented validation

Checks whether hypotheses, claims, and scenario implications have been exposed to meaningful failure conditions.

### 6. Robustness evaluation

Examines how outputs or conclusions behave under changed assumptions, parameters, or inputs.

### 7. Comparative evaluation

Compares artifacts, runs, scenarios, or reports against alternatives, baselines, or prior versions.

### 8. Historical evaluation

Checks artifact performance or plausibility against known historical cases or prior world states where relevant.

### 9. Interpretive evaluation

Assesses whether reports and outputs remain intelligible, decision-relevant, and caveated appropriately.

These families should not be collapsed into one generic idea of "review."

---

## Structural validation

## Purpose

Structural validation checks whether an artifact is sufficiently complete and well-formed to be processed responsibly.

## Typical questions

- Does the artifact contain the required fields?
- Does it follow the expected schema or minimum structure?
- Are required references present?
- Is the artifact type clearly identifiable?
- Are mandatory contracts satisfied?

## Typical targets

- hypotheses
- scenarios
- model specs
- run manifests
- validation records
- report bundles

## Why it matters

Structural weakness often creates downstream confusion that later gets mistaken for substantive complexity.

A malformed artifact should not be upgraded simply because its intent seems reasonable.

---

## Provenance validation

## Purpose

Provenance validation checks whether the origins and lineage of an artifact remain sufficiently visible and intact.

## Typical questions

- Can the artifact's source support be identified?
- Can key transformations be traced?
- Are upstream references preserved?
- Is machine-assisted transformation visible where relevant?
- Are missing provenance elements material?

## Typical targets

- curated input packages
- snapshots
- world snapshots
- hypotheses
- reports
- compressed context artifacts

## Why it matters

If provenance breaks, downstream confidence often becomes unjustified.

A polished downstream artifact cannot repair missing provenance retroactively.

---

## Admissibility validation

## Purpose

Admissibility validation checks whether an artifact is strong enough, bounded enough, and context-bound enough to remain in the active path.

## Typical questions

- Is the artifact tied to a concrete problem context?
- Are scope conditions explicit?
- Is the claim or representation epistemically bounded?
- Does the artifact avoid unbound generalization?
- Should processing continue, pause, or stop?

## Typical targets

- hypotheses
- scenarios
- reports
- synthesized context artifacts
- claims derived from model outputs

## Why it matters

This repository is not supposed to normalize context-free fluency as valid reasoning.

Admissibility validation is one of the mechanisms that protects against that drift.

---

## Consistency validation

## Purpose

Consistency validation checks whether an artifact or artifact set is internally coherent and mutually compatible.

## Typical questions

- Do the assumptions contradict each other?
- Does the scenario actually fit the linked hypotheses?
- Do model contracts match run usage?
- Do report claims overstep the underlying results?
- Are status and dependency references coherent?

## Typical targets

- scenario packages
- artifact chains
- run manifests
- report bundles
- linked hypothesis sets

## Why it matters

A repository can contain individually plausible artifacts that become incoherent when combined.

Consistency validation catches this class of failure.

---

## Falsification-oriented validation

## Purpose

Falsification-oriented validation checks whether a hypothesis or structured claim has been meaningfully exposed to possible failure.

## Typical questions

- What would count against this claim?
- Are counterindicators explicit?
- Are rival hypotheses considered?
- Are there observable implications that could break the claim?
- Is the artifact protected from failure only by vagueness?

## Typical targets

- hypotheses
- scenario-dependent claims
- report conclusions
- interpretation layers over outputs

## Why it matters

A claim that cannot fail in practice is often not a strong repository artifact.

This repository should prefer explicit vulnerability over protected ambiguity.

---

## Robustness evaluation

## Purpose

Robustness evaluation examines how outputs, conclusions, or recommendations behave when important assumptions change.

## Typical questions

- Does the result survive input perturbation?
- Does the conclusion collapse under a small parameter shift?
- Is the scenario highly sensitive to one arbitrary assumption?
- Are there stable patterns across alternative setups?
- Which assumptions are load-bearing?

## Typical targets

- runs
- result artifacts
- reports
- model-dependent conclusions
- scenario comparisons

## Why it matters

A result can be validly generated and still be too fragile for responsible use.

Robustness evaluation helps distinguish brittle output from stable insight.

---

## Comparative evaluation

## Purpose

Comparative evaluation examines whether an artifact is better, worse, narrower, broader, or otherwise different relative to alternatives.

## Typical questions

- Is this hypothesis stronger than the competing one?
- Does this scenario set outperform a simpler baseline?
- Does model revision improve explanatory value?
- Is the current report clearer or more traceable than the previous version?
- Does a more complex approach actually help?

## Typical targets

- competing hypotheses
- alternative scenarios
- model variants
- report versions
- multiple runs

## Why it matters

Without comparison, the repository may mistake "available" for "best available."

---

## Historical evaluation

## Purpose

Historical evaluation examines how artifact logic, scenario logic, or model behavior relates to known historical cases or prior states.

## Typical questions

- Would this framework have interpreted a past situation coherently?
- Does the hypothesis align with prior comparable cases?
- How would the model behave under a known historical transition?
- Are the outputs completely detached from historical structure?

## Typical targets

- hypotheses
- scenarios
- models
- run outputs
- evaluation frameworks

## Why it matters

Historical evaluation is not perfect validation, but it can expose implausible abstractions and weak assumptions.

---

## Interpretive evaluation

## Purpose

Interpretive evaluation assesses whether reports and summaries remain honest, useful, bounded, and decision-relevant.

## Typical questions

- Does the report overstate certainty?
- Are caveats visible enough?
- Are the key findings tied back to the artifact chain?
- Is the output interpretable without distortion?
- Does the narrative smuggle in unsupported claims?

## Typical targets

- reports
- executive summaries
- comparison summaries
- decision-facing outputs

## Why it matters

Good artifact chains can still be misrepresented in the final communicative layer.

Interpretive evaluation protects against that.

---

## Validation targets by artifact family

The following guidance is helpful as a repository baseline.

---

# 1. Input artifacts

## Key validation concerns

- provenance completeness
- scope clarity
- transformation lineage
- freshness awareness
- omission visibility

## Key evaluation concerns

- practical relevance
- coverage adequacy
- signal-to-noise quality
- suitability for snapshot use

---

# 2. World snapshots

## Key validation concerns

- explicit scope
- time reference clarity
- source support visibility
- distinction between observation and interpretation
- uncertainty visibility

## Key evaluation concerns

- adequacy for hypothesis work
- adequacy for scenario work
- coverage balance
- contextual usefulness

---

# 3. Hypotheses

## Key validation concerns

- explicit claim structure
- falsifiability
- mechanism clarity
- scope conditions
- provenance support
- counterindicator presence

## Key evaluation concerns

- explanatory value
- distinctiveness from alternatives
- relevance to scenario design
- usefulness for simulation or allocation reasoning

---

# 4. Scenarios

## Key validation concerns

- explicit assumptions
- time horizon
- actor identification
- linked hypothesis coherence
- branch legibility

## Key evaluation concerns

- breadth vs focus balance
- usefulness for consequence exploration
- sensitivity transparency
- decision relevance

---

# 5. Agents

## Key validation concerns

- role clarity
- abstraction-level clarity
- coherence with scenario logic
- explicit incentives and constraints

## Key evaluation concerns

- sufficiency for representing relevant behavior
- interpretive adequacy
- unnecessary complexity vs necessary detail

---

# 6. Models

## Key validation concerns

- contract compatibility
- assumption clarity
- input/output legibility
- failure mode declaration
- reconstructability

## Key evaluation concerns

- fit for purpose
- explanatory usefulness
- robustness
- sensitivity behavior
- interpretability

---

# 7. Runs

## Key validation concerns

- complete manifest
- exact artifact references
- reproducibility of execution context
- execution status visibility
- log availability

## Key evaluation concerns

- suitability of run design
- relevance to the problem question
- quality of parameterization choices

---

# 8. Results

## Key validation concerns

- linkage to run
- result integrity
- anomaly visibility
- output completeness

## Key evaluation concerns

- signal value
- robustness
- interpretability
- meaningfulness relative to the scenario and hypothesis set

---

# 9. Reports

## Key validation concerns

- traceability to artifact chain
- caveat visibility
- accurate status representation
- non-overstatement

## Key evaluation concerns

- clarity
- decision relevance
- comparative usefulness
- interpretive honesty

---

## Validation records

Validation and evaluation should not remain only in human memory or informal commentary.

Important checks should be captured as explicit validation records.

A validation record should make visible:

- target artifact(s)
- validation or evaluation type
- criteria used
- method used
- result or rating
- unresolved issues
- reviewer or origin
- timestamp

See also `docs/artifacts.md` and `docs/registries.md`.

---

## Recommended directory logic

A future structure could distinguish between technical and substantive checking, for example:

- `validation/`
  - `structural/`
  - `provenance/`
  - `admissibility/`
  - `consistency/`

- `evaluation/`
  - `robustness/`
  - `comparative/`
  - `historical/`
  - `interpretive/`

This exact layout can evolve.  
The important point is the conceptual distinction.

---

## Validation vs tests

Tests and validation are related but not identical.

### Tests

Tests usually check whether a technical component behaves as intended.

Examples:
- parser works
- schema validation works
- function returns expected structure
- runtime component handles failure correctly

### Validation

Validation checks whether an artifact, process, or result is acceptable under explicit repository criteria.

Examples:
- hypothesis is actually falsifiable
- snapshot provenance is adequate
- report does not overstate certainty
- run references are complete
- model assumptions remain visible

Technical tests belong mainly to implementation correctness.  
Validation belongs to repository governance and epistemic quality.

---

## Evaluation vs approval

Evaluation should not be confused with automatic approval.

A highly informative but fragile artifact may still receive a careful evaluation without being approved for strong downstream use.

Similarly:

- interesting does not mean active
- promising does not mean validated
- better than alternatives does not mean sufficient in absolute terms

The repository should preserve those distinctions.

---

## Pass/fail vs graded judgments

Not every validation or evaluation should use the same decision format.

A useful distinction is:

### Binary outcomes where appropriate

Good for:
- schema conformance
- required fields present
- provenance field exists
- run manifest has complete references

### Graded outcomes where appropriate

Good for:
- robustness
- interpretive quality
- explanatory value
- report usefulness
- historical adequacy

A flexible evaluation system is better than forcing everything into one simplistic pass/fail model.

---

## Recommended outcome vocabulary

The repository may eventually use outcome labels such as:

### For validation
- `passed`
- `failed`
- `partial`
- `blocked`
- `not_applicable`

### For evaluation
- `strong`
- `adequate`
- `limited`
- `weak`
- `inconclusive`

These are suggestions, not yet final schema requirements.

What matters is that outcomes remain explicit.

---

## Review intensity levels

Not every artifact requires the same depth of checking.

A useful distinction may be:

### Lightweight review

Used for early drafts, preliminary artifacts, or local structural checks.

### Standard review

Used for active artifacts intended for normal downstream dependency.

### High-stakes review

Used for artifacts supporting important runs, major reports, or externally visible conclusions.

The repository should not pretend all checks are equal.

---

## Stop conditions

Validation and evaluation must be able to stop progression.

Processing should stop, pause, or downgrade if, for example:

- provenance failure is material
- claim structure is too vague to validate
- scenario assumptions are contradictory
- model behavior is too opaque to audit responsibly
- result fragility is too high for the intended report claim
- report language overstates what the artifact chain supports
- unresolved issues remain load-bearing

If validation cannot affect progression, it becomes decorative.

---

## Partial acceptance and caveated use

Not all weak points require total rejection.

Sometimes the correct outcome is:

- accept with caveats
- allow internal exploration only
- downgrade to partial status
- restrict the use case
- require stronger caveating in reports
- prohibit strong claims while preserving exploratory value

This repository should allow qualified use without collapsing into all-or-nothing thinking.

---

## Competing hypotheses and rival explanations

Strong validation and evaluation should often include rival consideration.

Questions may include:

- Is there an alternative hypothesis that explains the same pattern better?
- Does a simpler scenario perform just as well?
- Is model complexity actually buying explanatory value?
- Are results robust across competing interpretations?

A repository that never compares rivals can easily become overattached to first formulations.

---

## Uncertainty handling

Validation and evaluation should not erase uncertainty.

Instead, they should help specify:

- where uncertainty sits
- whether it is tolerable for the intended use
- whether it is load-bearing
- whether it should block progression
- whether it should remain visible in downstream reports

The goal is not uncertainty elimination.  
The goal is uncertainty governance.

---

## Historical and forward-looking asymmetry

Some repository outputs concern historical or already-known conditions.  
Others concern future pathways or predictions.

Validation and evaluation should recognize this asymmetry.

### Historical cases

Can support:
- retrospective consistency checks
- known-outcome comparison
- replay-style robustness analysis

### Forward-looking cases

Must rely more on:
- assumption clarity
- rival hypotheses
- scenario breadth
- robustness analysis
- explicit uncertainty communication

The repository should not pretend future-facing outputs can be validated in the same way as historical ones.

---

## Review questions for major artifacts

Before a major artifact or report is treated as strong, the following kinds of questions should be answerable:

- What exactly was checked?
- Which criteria were used?
- Which issues remain unresolved?
- What kinds of use are justified?
- What kinds of use are not justified?
- How fragile is the artifact under changed assumptions?
- Does the report say more than the underlying artifact chain supports?

If these questions cannot be answered, the artifact is under-evaluated.

---

## Relationship to other canonical files

This file should be read together with:

- `docs/artifacts.md`
- `docs/ids-and-versioning.md`
- `docs/contracts.md`
- `docs/registries.md`
- `docs/data-governance.md`
- `docs/snapshots.md`

Those files define the artifact, identity, pipeline, governance, and input context within which validation and evaluation operate.

This file defines how strength, weakness, fitness, and failure should be assessed across that structure.

---

## Consequences for repository design

This file implies structural additions such as:

- explicit validation records
- clear distinction between tests and validation
- evaluation rubrics
- robustness analysis artifacts
- comparative review artifacts
- historical replay or benchmark structures
- report review logic

The repository does not need to implement all of this immediately.  
But it should be designed so these layers fit naturally.

---

## What this file does not define

This file defines the conceptual logic of validation and evaluation.

It does not yet define:

- final schemas for validation records
- exact scoring rubrics
- implementation-specific testing frameworks
- benchmark datasets
- review workflows in operational detail
- automation logic for evaluation pipelines

Those should be specified separately if needed.

---

## Status of this file

This file is canonical for:

- the distinction between validation and evaluation
- the main validation and evaluation families
- artifact-family-specific checking priorities
- the role of robustness, falsification, and interpretive honesty
- the expectation that checking can block progression

Any future review system in this repository should either:

- implement these distinctions directly, or
- document explicitly why an equivalent mechanism is being used instead
