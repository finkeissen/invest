# Stage Contracts of Invest-GT

## Purpose

This file defines the stage contracts of Invest-GT.

Its role is to make the repository pipeline structurally explicit before implementation begins.

A stage contract specifies:

- what a stage is allowed to consume
- what it is expected to produce
- which invariants must hold
- which failure conditions stop progression
- which artifacts may move forward
- which artifacts must be revised, rejected, or routed out of the active path

This file is canonical for stage boundaries.

---

## Why stage contracts matter

A pipeline is not made reliable merely by ordering folders numerically.

Without explicit stage contracts, typical failure modes include:

- outputs entering a downstream stage without sufficient structure
- hypotheses being used before they are explicit enough
- scenarios being assembled from unstable claims
- models being run against ambiguous inputs
- reports being produced without reconstructable execution context
- invalid artifacts flowing forward because no formal stop condition exists

This file exists to prevent that.

---

## General principle

Each pipeline stage must be interpreted as a constrained transformation layer.

A stage is not just a topic area.  
It is a bounded operation over artifacts.

Every stage should answer:

- What artifacts are admissible as inputs?
- What transformation is allowed here?
- What artifacts are valid outputs?
- What must be true before outputs may move on?
- Under which conditions must processing stop?

If these questions are not answerable, the stage is under-specified.

---

## Relationship to the broader architecture

Invest-GT is embedded in the broader Finkeissen research architecture.

That means stage progression is not governed only by local convenience.

It is governed by admissibility, provenance, explicit context binding, and auditability.

As a consequence:

- not every artifact may progress
- plausibility alone is insufficient
- unresolved ambiguity is not automatically acceptable
- failure to satisfy contract conditions must interrupt progression

Local stage contracts in this repository must not silently weaken upstream epistemic discipline.

---

## How to read this file

Each stage contract defines:

- purpose
- admissible inputs
- required input conditions
- allowed operations
- expected outputs
- output conditions
- stop conditions
- revision paths
- downstream dependencies

The stage numbers below reflect the current repository pipeline logic, but the core point is contractual separation, not numbering alone.

---

## Contract language

For clarity, this file uses the following terms.

### admissible input

An artifact that may validly enter the stage because it satisfies the stage's entry conditions.

### expected output

An artifact type that the stage is intended to produce when successful.

### invariant

A condition that must remain true throughout stage processing.

### stop condition

A condition under which the stage must not promote output downstream.

### revision path

The route an artifact takes when it is incomplete, weak, contradictory, or otherwise not yet promotable.

---

## Pipeline overview

A typical repository flow is:

1. inputs are gathered and bounded
2. a world snapshot is constructed
3. hypotheses are formed and constrained
4. scenarios are assembled
5. agent and model specifications are selected or defined
6. runs are configured and executed
7. results are captured
8. outputs are validated
9. reports are generated

This flow may branch or loop, but each transition should remain contract-governed.

---

# Stage 00 – Inputs

## Purpose

Stage 00 gathers, curates, bounds, and prepares the material from which a usable world-state representation can be built.

Its purpose is not merely collection.  
Its purpose is disciplined input preparation.

## Admissible inputs

Stage 00 may consume:

- raw source materials
- curated notes
- extracted observations
- source metadata
- manually assembled context packages
- domain-specific datasets
- prior admissible upstream references where appropriate

## Required input conditions

Inputs entering this stage should satisfy, as far as possible:

- identifiable origin
- minimally legible scope
- basic provenance information
- relevance to a concrete problem context or context-building task

Unidentified, decontextualized, or obviously irrelevant material should not enter active processing without being flagged.

## Allowed operations

Stage 00 may perform operations such as:

- collection
- filtering
- source registration
- extraction
- normalization
- grouping
- curation
- preliminary scope bounding
- uncertainty marking

## Expected outputs

Typical outputs of Stage 00 include:

- curated input bundles
- source registries
- extraction notes
- structured observation sets
- candidate input packages for world snapshot construction

## Output conditions

Outputs of Stage 00 should be:

- bounded enough to support explicit context building
- traceable to their sources
- tagged with uncertainty where needed
- distinguishable from interpretation and hypothesis

## Invariants

The following should remain true:

- provenance should not be erased
- extraction should not be silently upgraded into conclusion
- raw material and curated material should remain distinguishable

## Stop conditions

Processing should stop or loop for revision if:

- origin is unclear in a way that matters materially
- relevance to the intended problem context cannot be justified
- extraction quality is too poor to support snapshot construction
- conflicting inputs cannot even be represented explicitly
- inputs are too vague, too broad, or too unbounded to support disciplined use

## Revision path

Artifacts should return to:

- further curation
- scope refinement
- source clarification
- exclusion from active input sets

## Downstream dependency

Stage 00 supports Stage 01 by enabling explicit world-state construction.

---

# Stage 01 – World Snapshot Construction

## Purpose

Stage 01 constructs a bounded world-state artifact from prepared inputs.

Its job is to create a usable contextual basis for hypothesis formation and scenario design.

## Admissible inputs

Stage 01 may consume:

- curated input bundles from Stage 00
- source registries
- structured observations
- prior admissible context fragments where appropriate

## Required input conditions

Inputs should be:

- relevant to a concrete domain problem
- sufficiently curated to support synthesis
- traceable
- bounded in time, scope, and context

## Allowed operations

Stage 01 may perform operations such as:

- world-state synthesis
- contextual aggregation
- structural grouping
- uncertainty annotation
- omission recording
- scope declaration
- time-reference binding

## Expected outputs

Typical outputs include:

- a world snapshot
- snapshot metadata
- structured uncertainty notes
- omission and limitation notes

## Output conditions

A valid world snapshot should include:

- explicit scope
- time reference
- relevant domain coverage
- source traceability
- uncertainty markers
- distinction between observations and interpretations

## Invariants

The following should remain true:

- the snapshot is context-bound
- the snapshot is not silently converted into a forecast
- omitted areas are not disguised as nonexistent areas
- unresolved uncertainty remains visible

## Stop conditions

Processing should stop if:

- no coherent problem-bounded snapshot can be formed
- the scope is too broad to define a meaningful state representation
- provenance is too weak for core observations
- contradictory elements cannot be represented transparently
- the output collapses into narrative commentary instead of bounded state description

## Revision path

Artifacts should return to:

- input curation
- scope reduction
- source supplementation
- uncertainty clarification

## Downstream dependency

Stage 01 supports Stage 02 and Stage 03 by providing the contextual base for hypotheses and scenarios.

---

# Stage 02 – Hypothesis Formation

## Purpose

Stage 02 creates explicit, falsifiable, versionable hypotheses from world-state artifacts and admissible reasoning steps.

Its job is to transform contextual understanding into structured claims.

## Admissible inputs

Stage 02 may consume:

- world snapshots
- admissible prior hypotheses
- registered contextual artifacts
- explicit analytical notes derived from bounded sources

## Required input conditions

Inputs should provide enough structure to support:

- a claim
- a mechanism
- scope conditions
- possible falsification logic
- clear relation to the problem context

## Allowed operations

Stage 02 may perform operations such as:

- claim formation
- mechanism articulation
- assumption declaration
- dependency mapping
- counterindicator identification
- falsification framing
- confidence tagging

## Expected outputs

Typical outputs include:

- hypothesis artifacts
- hypothesis dependency notes
- comparison sets of competing hypotheses
- rejection or hold notes for weak candidate hypotheses

## Output conditions

A valid hypothesis should be:

- explicit
- bounded
- tied to a problem context
- falsifiable in principle
- distinguishable from general worldview statements
- traceable to upstream artifacts

## Invariants

The following should remain true:

- a hypothesis remains a claim, not a scenario
- uncertainty is not hidden behind confident wording
- unsupported generalization is not promoted as structured reasoning
- scope conditions remain visible

## Stop conditions

Processing should stop if:

- the claim cannot be stated clearly
- the claim is not meaningfully falsifiable
- the mechanism is too vague to evaluate
- the hypothesis depends on inadmissible upstream assumptions
- the artifact is rhetorical rather than operational
- provenance and context binding are too weak

## Revision path

Artifacts should return to:

- snapshot refinement
- narrower claim formulation
- explicit decomposition into multiple smaller hypotheses
- rejection or archival

## Downstream dependency

Stage 02 supports Stage 03, Stage 04, and Stage 05 by providing explicit claims that can be embedded in scenarios and models.

---

# Stage 03 – Scenario Construction

## Purpose

Stage 03 assembles structured possible world-paths under explicit assumptions, triggers, actors, and time horizons.

Its job is to build exploration contexts for simulation and consequence analysis.

## Admissible inputs

Stage 03 may consume:

- world snapshots
- admissible hypotheses
- problem statements
- actor context notes
- structural domain constraints

## Required input conditions

Inputs should support:

- a defined problem context
- an explicit time horizon
- meaningful assumptions
- identifiable relevant actors or systems
- at least one structured pathway worth exploring

## Allowed operations

Stage 03 may perform operations such as:

- assumption bundling
- trigger definition
- pathway construction
- branching logic definition
- actor relevance selection
- uncertainty boundary setting
- evaluation target definition

## Expected outputs

Typical outputs include:

- scenario artifacts
- branch descriptions
- linked hypothesis maps
- scenario assumption packages

## Output conditions

A valid scenario should include:

- a scenario identity
- clear scope
- time horizon
- triggering conditions
- relevant actors
- assumptions
- linked hypotheses
- uncertainty boundaries

## Invariants

The following should remain true:

- the scenario is not collapsed into one hypothesis
- assumptions are explicit
- branching structure is visible where relevant
- scenario design remains tied to the concrete problem

## Stop conditions

Processing should stop if:

- no coherent scenario frame can be specified
- assumptions are too implicit or contradictory
- linked hypotheses are too weak or too vague
- time horizon is undefined
- the artifact becomes a generic story instead of a structured exploration frame

## Revision path

Artifacts should return to:

- hypothesis refinement
- world snapshot refinement
- time-horizon narrowing
- actor selection clarification
- scenario decomposition

## Downstream dependency

Stage 03 supports Stage 04 and Stage 05 by defining the contextual frame for agents, models, and execution logic.

---

# Stage 04 – Agent and Model Specification

## Purpose

Stage 04 defines or selects the agents and models that will operationalize scenario dynamics and consequence logic.

Its job is to make the simulation structure explicit.

## Admissible inputs

Stage 04 may consume:

- scenarios
- world snapshots
- hypotheses
- methodological design notes
- prior validated agent or model specifications

## Required input conditions

Inputs should make clear:

- what kinds of actors matter
- what dynamics must be represented
- which transformations or interactions are required
- what level of abstraction is acceptable

## Allowed operations

Stage 04 may perform operations such as:

- agent definition
- model selection
- model design
- parameter framing
- interaction logic definition
- abstraction-level selection
- failure mode declaration

## Expected outputs

Typical outputs include:

- agent specifications
- model specifications
- dependency notes
- parameter assumptions
- model limitation notes

## Output conditions

A valid output should define:

- which agents exist
- what roles they have
- which models are used
- what each model consumes and produces
- what assumptions and limitations govern the setup

## Invariants

The following should remain true:

- agents remain distinct from models
- the abstraction level is explicit
- models are not treated as self-justifying
- limitations and simplifications remain visible

## Stop conditions

Processing should stop if:

- the chosen abstraction destroys the problem context
- required actors cannot be represented coherently
- model logic is opaque in a way that blocks auditability
- assumptions are too implicit
- no defensible mapping exists between scenario needs and operational structure

## Revision path

Artifacts should return to:

- scenario refinement
- hypothesis decomposition
- simpler or clearer model choice
- explicit admission that the current problem is not yet model-ready

## Downstream dependency

Stage 04 supports Stage 05 by producing the operational components needed for execution.

---

# Stage 05 – Run Configuration and Execution

## Purpose

Stage 05 binds the selected artifacts into one executable context and performs the actual run.

Its job is to convert conceptual structure into concrete execution.

## Admissible inputs

Stage 05 may consume:

- one or more world snapshots
- one or more active hypotheses
- one scenario
- selected agents
- selected models
- configuration files
- runtime parameters
- seeds where applicable

## Required input conditions

Inputs should be:

- versioned or otherwise stably identifiable
- compatible at the contract level
- sufficiently explicit for reconstruction
- bounded to one concrete execution purpose

## Allowed operations

Stage 05 may perform operations such as:

- manifest assembly
- configuration binding
- compatibility checks
- execution
- run logging
- failure capture
- deterministic or stochastic execution under explicit settings

## Expected outputs

Typical outputs include:

- run manifests
- execution logs
- raw result artifacts
- failure records
- system warnings

## Output conditions

A valid run output should include:

- run identity
- references to the exact artifact versions used
- configuration context
- execution status
- output references
- failure or warning notes where applicable

## Invariants

The following should remain true:

- no hidden dependency is silently introduced
- exact input references remain reconstructable
- execution state is recorded
- failures are not rewritten as successful outputs

## Stop conditions

Processing should stop if:

- required artifact references are missing
- incompatible artifacts are bound together
- the run cannot be reconstructed conceptually
- execution fails materially
- logging is insufficient for later audit

## Revision path

Artifacts should return to:

- model revision
- scenario revision
- config correction
- compatibility correction
- rerun as a new run artifact, not as silent overwrite

## Downstream dependency

Stage 05 supports Stage 06 and Stage 07 by generating concrete execution outputs.

---

# Stage 06 – Result Capture and Structuring

## Purpose

Stage 06 captures and structures the immediate outputs of execution before interpretation is layered onto them.

Its job is to preserve result integrity.

## Admissible inputs

Stage 06 may consume:

- completed runs
- raw execution outputs
- logs
- warnings
- failure traces
- intermediate result states where relevant

## Required input conditions

Inputs should have:

- a valid run reference
- sufficient execution metadata
- enough structure to distinguish result from interpretation

## Allowed operations

Stage 06 may perform operations such as:

- result packaging
- summary metric extraction
- state recording
- anomaly tagging
- output indexing
- trace bundling

## Expected outputs

Typical outputs include:

- result artifacts
- result summaries
- anomaly records
- structured output packages

## Output conditions

A valid result artifact should include:

- result identity
- run reference
- output references
- structural summary
- warnings or anomaly markers
- execution context linkage

## Invariants

The following should remain true:

- result capture is not rewritten as narrative conclusion
- anomalies remain visible
- missing outputs are not silently ignored
- linkage to the originating run remains intact

## Stop conditions

Processing should stop if:

- result integrity cannot be established
- the run-output linkage is broken
- outputs are too incomplete for structured review
- result packaging would require inventing missing data
- critical anomalies make downstream interpretation misleading

## Revision path

Artifacts should return to:

- rerun
- execution debugging
- output packaging correction
- explicit failure classification

## Downstream dependency

Stage 06 supports Stage 07 and Stage 08 by providing reviewable execution outputs.

---

# Stage 07 – Validation and Evaluation

## Purpose

Stage 07 checks whether artifacts, results, and interpretations hold up under explicit criteria.

Its job is not to guarantee certainty.  
Its job is to make checking explicit.

## Admissible inputs

Stage 07 may consume:

- world snapshots
- hypotheses
- scenarios
- models
- runs
- results
- report drafts
- validation criteria
- baseline references
- historical comparison data

## Required input conditions

Inputs should be:

- identifiable
- traceable
- explicit enough to be checked
- linked to stated validation criteria

## Allowed operations

Stage 07 may perform operations such as:

- schema validation
- consistency checking
- provenance checking
- robustness analysis
- falsification attempts
- historical comparison
- sensitivity analysis
- expert review
- issue recording

## Expected outputs

Typical outputs include:

- validation records
- pass/fail assessments
- partial validation notes
- issue logs
- robustness summaries
- invalidation notices

## Output conditions

A valid validation artifact should specify:

- what was checked
- how it was checked
- against which criteria
- with what result
- what remains unresolved

## Invariants

The following should remain true:

- validation criteria are explicit
- passing one check is not inflated into universal endorsement
- unresolved issues remain visible
- failed checks remain attached to the relevant artifact chain

## Stop conditions

Processing should stop if:

- no explicit validation criteria exist
- the target artifact is too vague to test
- provenance failure breaks the object under review
- major contradictions remain unresolved
- the result is too unstable for responsible reporting

## Revision path

Artifacts should return to:

- earlier stage correction
- narrower reporting
- explicit partial-status handling
- rejection or invalidation

## Downstream dependency

Stage 07 supports Stage 08 by determining what may responsibly be communicated and under what caveats.

---

# Stage 08 – Reporting

## Purpose

Stage 08 produces interpretable, audit-ready outputs from validated or reviewable artifact chains.

Its job is to communicate without breaking traceability.

## Admissible inputs

Stage 08 may consume:

- runs
- results
- validation records
- scenarios
- hypotheses
- world snapshots
- approved interpretation notes

## Required input conditions

Inputs should be:

- linked to explicit artifact references
- sufficiently validated or explicitly caveated
- bounded to a defined reporting purpose

## Allowed operations

Stage 08 may perform operations such as:

- summary generation
- interpretation
- comparison
- report assembly
- appendix generation
- traceability linking
- uncertainty communication

## Expected outputs

Typical outputs include:

- report bundles
- executive summaries
- technical summaries
- comparison reports
- audit appendices

## Output conditions

A valid report should include:

- report identity
- reporting scope
- referenced artifact chain
- key findings
- assumptions in force
- uncertainty and limitation notes
- traceability references

## Invariants

The following should remain true:

- reports remain tied to artifacts
- uncertainty is not erased for rhetorical clarity
- interpretation does not silently replace result content
- caveats remain visible where required

## Stop conditions

Processing should stop if:

- the report cannot be tied to a concrete artifact chain
- uncertainty is too high to support the intended claim form
- validation status is misrepresented
- key assumptions are missing
- the output would overstate what the pipeline actually supports

## Revision path

Artifacts should return to:

- narrower reporting scope
- stronger caveating
- additional validation
- upstream artifact clarification
- refusal to publish the claim in its current form

## Downstream dependency

Reports may support review, comparison, archival use, and further decision analysis, but they should not be treated as source substitutes.

---

# Cross-stage invariants

The following invariants apply across the full pipeline.

## 1. Context binding must remain explicit

No stage should promote artifacts that have lost their problem context.

## 2. Provenance must remain recoverable

No stage should erase origin in a way that blocks auditability.

## 3. Artifact distinctions must remain legible

A hypothesis must not become a scenario by accident.  
A result must not become a report by accident.

## 4. Failure must remain representable

A failed run, rejected hypothesis, invalidated artifact, or unresolved contradiction must remain visible as such.

## 5. Ambiguity must not be hidden by fluency

A well-written artifact is not automatically a strong artifact.

## 6. Downstream convenience does not override contract rules

An artifact should not move forward merely because the next stage would benefit from having something to work with.

---

# Contract failure handling

When a stage contract fails, there are only a limited number of legitimate outcomes.

## Possible outcomes

- revise the artifact
- narrow the scope
- split the artifact into smaller artifacts
- mark the artifact as draft or partial
- reject the artifact
- invalidate the artifact
- archive the artifact
- stop progression

The correct response depends on the failure mode, but silent progression should not be an option.

---

# Minimal contract checklist for every stage

Every stage should eventually be implementable against the following minimal checklist:

- Are the inputs explicitly listed?
- Are the outputs explicitly listed?
- Are input conditions defined?
- Are output conditions defined?
- Are invariants stated?
- Are stop conditions stated?
- Is the revision path stated?
- Are downstream dependencies stated?

If not, the stage remains only informally defined.

---

# Consequences for repository implementation

This contract logic suggests future repository structures such as:

- stage-local `spec.yaml` files
- explicit input/output schemas
- contract tests
- run-time compatibility checks
- validation gates
- manifest-based reporting

This file is canonical for conceptual contract boundaries.  
Operational implementation may later refine it, but should not contradict it silently.

---

# What this file does not define

This file defines stage-level contract logic.

It does not yet define:

- exact schema fields per artifact
- code-level interfaces
- runtime orchestration logic
- detailed validation methodology
- file storage conventions
- registry implementation

These should be specified separately.

---

# Status of this file

This file is canonical for:

- stage boundary logic
- stage responsibilities
- stage stop conditions
- cross-stage invariants

Whenever a new major pipeline stage is introduced, it should either:

- fit this contract model, or
- document explicitly why a different contract structure is required
