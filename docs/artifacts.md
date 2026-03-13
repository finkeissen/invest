# Canonical Artifacts of Invest-GT

## Purpose

This file defines the main artifact types used in Invest-GT.

Its role is to make the repository structurally legible before implementation begins.

The repository should not be understood merely as a collection of folders or workflow stages.  
It should be understood as a system that produces, transforms, validates, and audits explicit artifacts.

These artifacts are the durable units of reasoning, simulation, and reporting.

They must therefore be defined clearly and used consistently.

---

## Why artifact definitions matter

Without explicit artifact definitions, a repository like this tends to drift into ambiguity.

Typical forms of ambiguity include:

- a hypothesis being treated like a scenario
- a scenario being treated like a simulation run
- a model being confused with an agent
- a report mixing conclusions with raw observations
- inputs being used without a stable snapshot identity
- outputs being generated without a reconstructable artifact path

This file exists to prevent that drift.

---

## General rule

An artifact in Invest-GT is only valid if it has:

- a clear purpose
- an identifiable boundary
- explicit provenance
- a stable identity
- a defined relation to upstream and downstream artifacts

No major repository object should remain only implicit.

---

## Artifact families

The main artifact families in this repository are:

1. world-state artifacts
2. hypothesis artifacts
3. scenario artifacts
4. agent artifacts
5. model artifacts
6. run artifacts
7. result artifacts
8. report artifacts
9. validation artifacts

These families are related but not interchangeable.

---

## 1. World-state artifacts

### Name

**World Snapshot**

### Purpose

A world snapshot captures the relevant state of the world for a given problem context at a defined point in time or within a defined temporal window.

It provides the contextual basis from which hypotheses, scenarios, and simulations can be constructed.

### What it is

A world snapshot is a structured representation of relevant conditions such as:

- political context
- macroeconomic context
- industrial context
- technological context
- institutional context
- infrastructure and dependency context
- conflict and security context

### What it is not

A world snapshot is not:

- a general encyclopedia
- a stream of unfiltered facts
- a narrative essay
- a forecast
- a policy recommendation

It is a bounded context artifact.

### Typical contents

A world snapshot should typically contain:

- snapshot identifier
- scope statement
- time reference
- included domains
- source references
- admissibility/provenance notes
- structured observations
- known uncertainties
- omitted areas

### Upstream relation

World snapshots usually originate from curated inputs, source materials, extracted observations, and context selection decisions.

### Downstream relation

World snapshots are used to support:

- hypothesis formation
- scenario construction
- simulation setup
- report contextualization

### Canonical question

What is the relevant state of the world, for this problem, under explicit scope and time constraints?

---

## 2. Hypothesis artifacts

### Name

**Hypothesis**

### Purpose

A hypothesis is a versioned, explicit, falsifiable claim about a mechanism, directional effect, behavioral response, structural change, or consequence pattern.

### What it is

A hypothesis formalizes a claim that can be tested, challenged, refined, compared, or rejected.

It should express more than a vague intuition and less than a final conclusion.

### What it is not

A hypothesis is not:

- a free-floating opinion
- a broad worldview statement
- a scenario
- a prediction
- a report conclusion

### Typical contents

A hypothesis should typically contain:

- hypothesis identifier
- title
- claim statement
- mechanism description
- scope conditions
- assumptions
- expected implications
- counterindicators
- falsification conditions
- confidence status
- dependencies on other artifacts
- provenance links

### Upstream relation

Hypotheses are grounded in world snapshots, prior registered artifacts, and admissible reasoning steps.

### Downstream relation

Hypotheses can inform:

- scenario generation
- model selection
- simulation design
- prediction logic
- reporting

### Canonical question

What explicit claim are we making here, under which assumptions, and how could it fail?

---

## 3. Scenario artifacts

### Name

**Scenario**

### Purpose

A scenario defines a structured possible world-path under explicit assumptions, actor conditions, triggers, and temporal logic.

### What it is

A scenario is a bounded arrangement of conditions under which hypotheses can be explored and consequences can be simulated.

It provides a structured context for dynamic reasoning.

### What it is not

A scenario is not:

- a single hypothesis
- a raw input bundle
- a model implementation
- a specific run result
- a generic story

### Typical contents

A scenario should typically contain:

- scenario identifier
- scenario title
- problem context
- time horizon
- triggering conditions
- relevant actors
- assumptions
- constraints
- linked hypotheses
- key branches or pathways
- uncertainty boundaries
- evaluation goals

### Upstream relation

Scenarios are constructed from world snapshots and sets of admissible hypotheses.

### Downstream relation

Scenarios define the frame for:

- agent activation
- model use
- run configuration
- consequence analysis

### Canonical question

Under which structured set of assumptions and conditions are we exploring possible developments?

---

## 4. Agent artifacts

### Name

**Agent Specification**

### Purpose

An agent specification defines a relevant actor in a form suitable for simulation or structured reasoning.

### What it is

An agent represents an entity with incentives, constraints, capabilities, preferences, and possible responses.

Depending on context, an agent may be:

- a state
- a firm
- an institution
- an alliance
- a regulator
- a sector-level actor
- another strategically relevant entity

### What it is not

An agent is not:

- a model
- a scenario
- a full world snapshot
- a narrative role label without structure

### Typical contents

An agent specification should typically contain:

- agent identifier
- agent type
- scope and role
- relevant objectives
- constraints
- resources or capabilities
- adaptation rules
- decision variables
- known dependencies
- uncertainty notes

### Upstream relation

Agent specifications depend on problem context, world-state representation, and scenario design.

### Downstream relation

Agents are used by model components and simulation logic.

### Canonical question

Who are the relevant actors here, and how are their incentives and constraints represented?

---

## 5. Model artifacts

### Name

**Model Specification**

### Purpose

A model specification defines the formal or semi-formal logic used to simulate, infer, transform, or score within the repository.

### What it is

A model is the structure that operationalizes relationships, dynamics, or transformations.

A model may represent:

- causal logic
- state transition logic
- allocation logic
- interaction rules
- scoring rules
- update rules
- aggregation rules

### What it is not

A model is not:

- an agent
- a scenario
- a run
- a report
- a raw code module without conceptual definition

### Typical contents

A model specification should typically contain:

- model identifier
- model purpose
- formalism or method
- inputs
- outputs
- assumptions
- constraints
- parameter notes
- failure modes
- validation notes

### Upstream relation

Model specifications are chosen or built based on scenario needs, artifact contracts, and methodological decisions.

### Downstream relation

Models are instantiated during runs and contribute to result generation.

### Canonical question

What transformation or dynamic structure are we using, and under what assumptions does it operate?

---

## 6. Run artifacts

### Name

**Run Manifest**

### Purpose

A run manifest records one concrete execution instance of the repository logic.

### What it is

A run manifest is the reproducibility spine of an execution.

It identifies exactly what was used, under which configuration, for what purpose, and with which dependencies.

### What it is not

A run manifest is not:

- a scenario definition
- a model specification
- a result summary
- a report narrative

### Typical contents

A run manifest should typically contain:

- run identifier
- execution date/time
- operator or origin
- linked world snapshot
- linked hypotheses
- linked scenario
- linked agents
- linked models
- config references
- seed information where relevant
- runtime notes
- execution purpose
- output locations
- status

### Upstream relation

Run manifests bind together the upstream artifact set into one executable configuration.

### Downstream relation

Run manifests produce results and enable audit/reconstruction.

### Canonical question

What exactly was executed, using which artifact versions and settings?

---

## 7. Result artifacts

### Name

**Simulation Result**

### Purpose

A simulation result captures the immediate outputs of a concrete run.

### What it is

A result is the direct execution product generated from a run under a defined setup.

It may include:

- trajectories
- states
- scores
- outcome distributions
- sensitivity outputs
- event chains
- allocation implications
- failure records

### What it is not

A result is not:

- automatically a validated conclusion
- a hypothesis
- a scenario
- a polished report

### Typical contents

A result should typically contain:

- result identifier
- linked run identifier
- output data references
- summary metrics
- notable events or states
- warnings
- uncertainty markers
- execution anomalies

### Upstream relation

Results are downstream of concrete run manifests.

### Downstream relation

Results may feed into:

- evaluation
- comparison
- validation
- reporting

### Canonical question

What came out of this specific run before interpretation is layered on top?

---

## 8. Report artifacts

### Name

**Report Bundle**

### Purpose

A report bundle translates artifact chains and results into interpretable, audit-ready output for review, comparison, or communication.

### What it is

A report bundle is a structured interpretive artifact built from upstream validated or inspectable materials.

It should remain tied to the actual artifact chain.

### What it is not

A report is not:

- a raw run dump
- an unconstrained opinion piece
- a source substitute
- a detached executive summary without traceability

### Typical contents

A report bundle should typically contain:

- report identifier
- linked run/result references
- scope statement
- summary of question addressed
- key findings
- assumptions in force
- uncertainty statements
- interpretation notes
- limitations
- traceability references
- appendices or linked artifacts

### Upstream relation

Reports depend on runs, results, scenarios, hypotheses, and world-state artifacts.

### Downstream relation

Reports may support decision review, archival comparison, further investigation, or validation discussions.

### Canonical question

What should a reviewer understand from this artifact chain, and how can that understanding be audited?

---

## 9. Validation artifacts

### Name

**Validation Record**

### Purpose

A validation record documents checks performed against artifacts, runs, outputs, or claims.

### What it is

A validation record is an explicit record of how an artifact or output was examined.

Validation may include:

- schema checks
- consistency checks
- provenance checks
- historical comparison
- falsification attempts
- robustness tests
- sensitivity analysis
- expert review notes

### What it is not

A validation record is not:

- a casual comment
- a hidden internal assumption
- a vague statement that something "looks right"

### Typical contents

A validation record should typically contain:

- validation identifier
- target artifact(s)
- validation type
- criteria used
- method used
- findings
- pass/fail or graded outcome
- unresolved issues
- reviewer or execution source
- timestamp

### Upstream relation

Validation records consume artifacts that need to be checked.

### Downstream relation

Validation records influence whether artifacts are promoted, revised, rejected, or flagged.

### Canonical question

What exactly was checked, how was it checked, and what was the result?

---

## Artifact identity requirements

Every canonical artifact should eventually support a stable identity model.

At minimum, major artifacts should have:

- artifact type
- unique identifier
- version or revision indicator
- creation timestamp
- update timestamp where relevant
- provenance reference
- status indicator

Examples of possible identifiers:

- `SNAP-001`
- `HYP-014`
- `SCN-003`
- `AGT-007`
- `MOD-005`
- `RUN-20260312-001`
- `RES-20260312-001`
- `RPT-20260312-001`
- `VAL-20260312-001`

The exact naming convention can be specified separately, but stable identity is non-optional.

---

## Artifact status

Major artifacts should also carry explicit status where applicable.

Typical statuses may include:

- draft
- active
- deprecated
- rejected
- archived
- invalidated
- superseded

The allowed status model may vary by artifact family.

For example:

- hypotheses may be draft, active, rejected, superseded
- scenarios may be draft, active, archived
- runs may be planned, executed, failed
- validation records may be open, passed, failed, partial

---

## Canonical artifact path

A typical artifact chain in Invest-GT may look like this:

1. inputs are gathered and curated
2. a world snapshot is created
3. hypotheses are formulated
4. a scenario is assembled
5. agent and model specifications are selected
6. a run manifest is generated
7. a simulation produces results
8. results are evaluated and validated
9. a report bundle is produced

This path may branch or loop, but it should never become opaque.

---

## Separation rules

The following separations should remain strict.

### Hypothesis vs Scenario

A hypothesis is a claim.  
A scenario is a structured possible context or pathway.

### Agent vs Model

An agent is an actor representation.  
A model is a transformation or dynamic logic.

### Run vs Result

A run is the execution instance.  
A result is what the run produced.

### Result vs Report

A result is immediate output.  
A report is structured interpretation tied back to the artifact chain.

### Validation vs Conclusion

Validation checks whether something holds up under explicit criteria.  
It does not automatically settle every substantive interpretation.

---

## Minimum admissibility expectation for artifacts

An artifact should not be treated as part of the repository core unless it can answer, at minimum:

- What am I?
- Why do I exist?
- Where did I come from?
- What do I depend on?
- What can depend on me?
- Under which assumptions am I valid?
- How can I be checked?

If these questions cannot be answered, the artifact is structurally weak.

---

## Consequences for repository design

Because artifacts are primary, the repository should gradually evolve toward:

- explicit schemas
- registries
- contracts between stages
- version tracking
- validation records
- run manifests
- reproducible report generation

Folder structure alone is not sufficient.

The repository should be organized so that artifacts are not only stored, but governed.

---

## What this file does not define

This file defines artifact categories and boundaries.

It does not yet define:

- exact schema fields
- storage format choices
- naming conventions in final form
- stage-by-stage contracts
- implementation details
- runtime interfaces

Those should be defined in separate files.

---

## Status of this file

This file is canonical for artifact vocabulary and artifact boundaries.

Whenever a new major object is introduced into the repository, it should either:

- fit one of the artifact types defined here, or
- be introduced explicitly as a new artifact type with clear justification
