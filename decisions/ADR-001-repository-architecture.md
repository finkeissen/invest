# ADR-001: Repository Architecture as an Artifact-Governed, Constraint-Bound Pipeline

## Status

Accepted

---

## Date

2026-03-12

---

## Context

Invest-GT is not intended to be a loose collection of notes, scripts, and exploratory simulations.

It is intended to become a domain-specific research and simulation repository inside the broader Finkeissen research architecture.

That broader architecture places strong emphasis on:

- context-bound admissibility
- provenance visibility
- explicit stop conditions
- auditable knowledge handling
- resistance to unbound generalization
- explicit governance of artifacts and claims

Within that larger context, Invest-GT focuses on investment-relevant world modeling, hypothesis construction, scenario building, simulation, and allocation-oriented consequence analysis.

At the repository level, an early architectural choice is required:

Should the repository be structured mainly as:
- an implementation-first codebase,
- a collection of domain documents,
- a notebook-driven research space,
- or an explicit artifact-governed pipeline?

This decision matters because the repository's structure will strongly influence:

- what counts as a canonical object
- how reasoning becomes formalized
- how reproducibility is achieved
- how simulations are interpreted
- how reports remain auditable
- whether epistemic discipline is preserved once implementation begins

Without a clear decision, the repository risks drifting into a hybrid structure in which:
- conceptual objects remain implicit
- code becomes the hidden source of truth
- assumptions are distributed across docs, filenames, and local memory
- runs become hard to reconstruct
- reports overstate what the underlying artifact chain actually supports

A foundational architectural decision is therefore needed.

---

## Decision

Invest-GT will be structured as an **artifact-governed, constraint-bound pipeline repository**.

This means the repository will be designed around explicit canonical artifacts and governed transitions between them, rather than around code modules alone, document folders alone, or notebook workflows alone.

The repository architecture will therefore prioritize:

1. explicit artifact families
2. stable artifact identity
3. stage contracts
4. governed input and snapshot logic
5. run manifests for execution binding
6. validation and evaluation as first-class layers
7. reports as downstream governed artifacts rather than free narrative endpoints

The repository will be understood as a pipeline not merely because it has ordered folders, but because each stage transforms governed artifacts under explicit constraints.

The repository will also be understood as constraint-bound because progression is not automatic.

Artifacts may be:
- revised
- rejected
- invalidated
- archived
- stopped from progressing downstream

Plausibility, fluency, or convenience are not sufficient reasons for promotion.

---

## Architectural interpretation

This decision implies that the repository's primary structural unit is the **artifact**, not the file, not the folder, not the notebook, and not the function in isolation.

Files and directories are important implementation and organization mechanisms, but they are secondary to the canonical artifact model.

For example:

- a hypothesis is not just "a markdown file in `hypotheses/`"
- a scenario is not just "a folder with notes"
- a run is not just "something that happened in code"
- a report is not just "a narrative document"

Each of these is treated as a governed artifact with:
- identity
- scope
- dependencies
- lifecycle status
- validation relevance
- downstream consequences

This repository will therefore evolve toward explicit artifact governance even if implementation begins in a relatively lightweight form.

---

## Consequences

### 1. Artifact definitions become canonical

The repository will require canonical definitions for major artifact families such as:

- world snapshots
- hypotheses
- scenarios
- agents
- models
- run manifests
- results
- reports
- validation records

This is why files such as `docs/artifacts.md` are foundational rather than optional.

### 2. Stable IDs and lifecycle status become necessary

Artifacts will need stable IDs, status fields, and version logic.

This avoids ambiguity such as:
- which hypothesis is active
- which scenario version was used
- whether a model is deprecated
- whether a report is still valid

### 3. Stage boundaries must be explicit

The repository will need explicit stage contracts that define:

- admissible inputs
- expected outputs
- invariants
- stop conditions
- revision paths

This prevents folder order from being mistaken for genuine process discipline.

### 4. Input governance becomes part of the architecture

Because downstream artifact strength depends on input strength, the repository must explicitly distinguish between:

- raw inputs
- curated inputs
- canonical inputs
- snapshots

This makes the input layer part of the epistemic architecture, not just a storage problem.

### 5. Execution must be manifest-based

Concrete runs must be represented by run manifests that bind:

- snapshots
- world snapshots where relevant
- hypotheses
- scenarios
- agents
- models
- configs
- outputs

This is essential for reproducibility and auditability.

### 6. Validation and evaluation become first-class repository layers

Validation and evaluation will not be treated as optional polish after "real work" is done.

They will be part of the architectural design from the beginning.

### 7. Reports remain downstream, bounded, and traceable

Reports will be treated as governed interpretive artifacts rather than free-floating essays.

This protects the repository from losing rigor at the final communication step.

### 8. Code becomes one layer, not the whole architecture

Implementation code will matter, but it will not be allowed to silently become the only real source of truth.

Conceptual structure must remain visible outside the code.

---

## What this decision rejects

This decision explicitly rejects several weaker architectural alternatives.

### Rejected alternative 1: implementation-first repository

Under this model, the "real" structure would live mainly in code, with documentation following later.

This was rejected because it would make:
- assumptions harder to inspect
- reasoning structure easier to hide
- artifact identity weaker
- auditability harder to preserve
- epistemic governance dependent on implementation details

### Rejected alternative 2: documentation-only conceptual repository

Under this model, the repository would remain mainly a design space without strong artifact or execution governance.

This was rejected because it would risk:
- persistent ambiguity
- weak reproducibility
- poor run traceability
- difficulty bridging from theory to execution

### Rejected alternative 3: notebook-centric research flow

Under this model, notebooks would become the main space where real logic emerges.

This was rejected as the dominant architecture because notebook-centric development often leads to:
- hidden state
- weak artifact boundaries
- poor reuse discipline
- fragile reproducibility
- hard-to-audit transitions from exploration to accepted artifacts

Notebooks may still exist, but only as secondary research tools.

### Rejected alternative 4: folder-order-as-pipeline

Under this model, numerical folder ordering would be treated as sufficient process structure.

This was rejected because ordered folders without explicit contracts are not a reliable architecture.

---

## Why this decision fits Invest-GT specifically

Invest-GT deals with a domain where several risks are unusually strong:

- unstable world conditions
- mixed qualitative and quantitative inputs
- strong temptation toward rhetorical macro narrative
- uncertainty-heavy causal claims
- simulation outputs that are easy to overinterpret
- allocation implications that may appear more precise than they are

An artifact-governed, constraint-bound architecture is especially appropriate in this domain because it creates pressure toward:

- explicit assumptions
- bounded claims
- visible uncertainty
- reproducible execution
- explicit dependency tracking
- disciplined report generation

This architecture is not a luxury in this repository.  
It is a defense against predictable failure modes.

---

## Trade-offs

This decision has real costs.

### Cost 1: more upfront structure

The repository must define concepts and interfaces before implementation becomes extensive.

### Cost 2: slower informal iteration

Some exploratory work that would be quick in a looser structure must be formalized before being promoted.

### Cost 3: more governance overhead

IDs, statuses, manifests, registries, and validation layers require maintenance.

### Cost 4: less tolerance for hidden convenience

Fast but opaque shortcuts become less acceptable.

These costs are accepted because they buy:

- clearer reasoning structure
- stronger reproducibility
- better auditability
- less semantic drift
- safer transition from concept to implementation

---

## Practical implications for repository evolution

This decision implies that the repository should gradually add and stabilize at least the following:

- canonical conceptual docs for artifacts, contracts, snapshots, reports, validation, configuration
- registry structures
- snapshot logic
- run manifests
- validation records
- explicit config separation
- architecture decisions
- eventual schemas and implementation bindings

This does not require building everything at once.

But it does mean that new repository additions should be judged against this architecture.

The key question should be:

> does this strengthen or weaken artifact-governed, constraint-bound operation?

---

## Consequences for future decisions

Future ADRs should be interpreted under this architectural baseline.

In particular, future decisions about:

- code structure
- config handling
- schema design
- validation workflows
- registry implementation
- notebook usage
- report generation
- local vs canonical state

should be expected to align with this decision unless explicitly superseded.

---

## Non-goals of this decision

This decision does **not** yet define:

- exact schemas
- specific file formats
- programming language choices
- runtime orchestration tools
- storage backends
- CLI design
- automation level
- user interface design

Those belong in later decisions.

This decision defines the governing architecture, not the full implementation plan.

---

## Review rule

Any future proposal that would:

- hide conceptual meaning in implementation details
- weaken artifact identity
- bypass stage contracts
- make runs harder to reconstruct
- dissolve validation into informal judgment
- turn reports into detached narratives

should be treated as conflicting with this ADR unless explicitly justified and accepted through a later architectural decision.

---

## Summary

Invest-GT is intentionally being designed as an artifact-governed, constraint-bound pipeline repository.

This means:

- artifacts come first
- transitions are governed
- progression is conditional
- execution must be reconstructable
- reporting must remain traceable
- implementation must serve the architecture rather than replace it

This decision is foundational and should be treated as one of the core architectural commitments of the repository.
