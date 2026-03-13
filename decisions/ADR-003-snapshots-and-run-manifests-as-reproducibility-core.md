# ADR-003: Snapshots and Run Manifests as the Reproducibility Core

## Status

Accepted

---

## Date

2026-03-12

---

## Context

Invest-GT is being developed as an artifact-governed, constraint-bound pipeline repository.

Under that architecture, reproducibility and auditability are not optional quality improvements.  
They are structural requirements.

However, reproducibility in a repository like this is not trivial.

Invest-GT operates on:

- changing world conditions
- curated and partially interpreted inputs
- scenario-dependent execution contexts
- multiple artifact families with separate identities
- configuration layers
- exploratory and report-supporting runs
- outputs that may later support reports, comparison, or decisions

Without a clear reproducibility core, several predictable problems arise:

- runs refer to "current data" rather than a frozen governed input state
- execution context depends on artifact sets that are not explicitly bound together
- reports rely on outputs whose input basis cannot later be reconstructed
- comparisons between runs become ambiguous because input or config drift is invisible
- later reviewers can see results, but not the exact conditions that produced them
- historical replay or backtesting logic becomes structurally weak

A foundational decision is therefore needed:

What should count as the repository's core reproducibility mechanism?

---

## Decision

Invest-GT will treat **snapshots** and **run manifests** as the core reproducibility pair of the repository.

The repository's reproducibility logic will therefore be built around two distinct but tightly connected artifact types:

1. **Snapshots**  
   governed freezes of relevant input state

2. **Run manifests**  
   governed bindings of concrete execution context

The core rule is:

> no materially important run without an explicit run manifest, and no materially input-sensitive run without explicit snapshot reference

This means:

- snapshots preserve the governed input basis
- run manifests preserve the governed execution binding
- together they form the minimum reproducibility spine for downstream results and reports

---

## Interpretation

This decision intentionally separates two problems that are often blurred.

### Problem 1: What input state was in force?

This is the job of the snapshot.

### Problem 2: What was actually executed?

This is the job of the run manifest.

Both are necessary.

A run manifest without snapshot discipline leaves input drift unresolved.  
A snapshot without run-manifest discipline leaves execution binding unresolved.

The repository therefore adopts both as co-equal reproducibility pillars.

---

## Why this pair is necessary

Many repositories try to solve reproducibility using only one of the following:

- code version
- current data folder
- a config file
- a notebook
- a log
- a model checkpoint
- a report appendix
- a result filename

Each of these may help, but none of them is sufficient here.

### Code version alone is insufficient

The same code can produce materially different meaning under different:
- inputs
- scenarios
- hypotheses
- configs
- seeds
- artifact selections

### Current folder state is insufficient

The folder state changes over time and does not preserve bounded historical context.

### Config alone is insufficient

A config may control execution details, but it does not freeze the governed input state or replace artifact identity.

### Logs alone are insufficient

Logs may record execution events, but often do not preserve the conceptual artifact bundle or input freeze properly.

### Reports are downstream, not execution truth

Reports summarize and interpret.  
They are not the right place to define execution history.

This is why the repository needs both snapshots and run manifests explicitly.

---

## Snapshot role

Snapshots preserve the answer to:

> Which governed input state was active for this work?

A snapshot is not a generic backup and not merely "the data at that time."

It is a governed freeze of relevant input state under explicit scope and time reference.

A snapshot should preserve things such as:

- included input refs
- excluded or omitted materials where relevant
- scope
- time reference
- lineage
- uncertainty notes

This makes the input basis legible and historically meaningful.

---

## Run manifest role

Run manifests preserve the answer to:

> Which artifacts, configurations, and runtime conditions were bound into this concrete execution?

A run manifest is not merely a config and not merely a log.

It is the governed artifact that records:

- which snapshots were used
- which world snapshots were used where relevant
- which hypotheses were in force
- which scenario was instantiated
- which agents and models were selected
- which config governed execution
- which runtime mode and seed conditions applied
- what outputs were produced
- what status the run had

This makes the execution context reconstructable.

---

## Core reproducibility rule

The repository adopts the following rule:

> a materially meaningful result should always be attributable to a run manifest, and a materially input-sensitive run should always be attributable to one or more snapshots

This rule is intentionally stronger than:

- "we can probably infer what happened"
- "the defaults were probably used"
- "the notebook makes it clear enough"
- "the folder state still exists"

Inference is not enough for core repository reproducibility.

---

## Consequences

### 1. Snapshots become first-class artifacts

Snapshots will not be treated as an implementation detail or optional convenience.

They will be first-class governed artifacts with:
- identity
- scope
- lifecycle
- downstream references

### 2. Run manifests become mandatory for important execution

Important runs must not exist only as:
- scripts that were called once
- notebook cells that produced output
- logs without explicit binding
- remembered configuration states

Run manifests become the canonical execution-binding record.

### 3. Results become dependent artifacts

A result should not stand alone.

A result should be attributable to:
- a run manifest
- and, where relevant, the snapshots referenced by that run

### 4. Reports remain traceable through the reproducibility core

A report that depends on runs should be traceable back through:
- report → result → run manifest → snapshot(s)

This becomes the minimum audit chain.

### 5. Comparative work becomes stronger

Comparisons between runs become more meaningful because reviewers can distinguish:
- changed input basis
- changed artifact bundle
- changed config
- changed runtime mode

### 6. Historical replay becomes possible in a governed way

Snapshots make historical input state explicit.  
Run manifests make historical execution explicit.

This is especially valuable for replay, validation, and comparison work.

---

## What this decision rejects

### Rejected alternative 1: reproducibility by code version only

This was rejected because code identity does not preserve:
- input state
- scenario state
- hypothesis state
- config state
- artifact bundle selection

### Rejected alternative 2: reproducibility by current canonical folders

This was rejected because current folder state is mutable and often does not preserve historical context.

### Rejected alternative 3: reproducibility by config only

This was rejected because config does not replace:
- governed input freeze
- artifact identities
- scenario selection
- run-specific output linkage

### Rejected alternative 4: notebook-as-manifest

This was rejected because notebooks are useful exploratory tools but poor as the canonical reproducibility core due to:
- hidden state
- execution-order fragility
- weak lifecycle governance
- poor identity discipline

### Rejected alternative 5: reports as sufficient execution history

This was rejected because reports are downstream interpretive artifacts and should not be forced to carry the full burden of execution truth.

---

## Why snapshots and run manifests are distinct

This ADR intentionally preserves a conceptual separation between:

### Input reproducibility

What was the governed input state?

### Execution reproducibility

What was the governed execution binding?

These are not the same question.

A repository that collapses them into one artifact often becomes harder to understand and maintain.

For example:

- the same snapshot may support multiple runs
- the same run pattern may be executed against different snapshots
- one report may compare runs that share models but differ in input state
- one scenario may be rerun under a new snapshot

Keeping snapshots and run manifests distinct supports these legitimate patterns cleanly.

---

## Link to world snapshots

This ADR does not collapse input snapshots and world snapshots into one artifact type.

The repository retains the distinction:

- **Snapshot** = governed frozen input basis
- **World snapshot** = synthesized contextual world-state representation

A run may reference both.

This distinction is useful because the repository often needs to preserve both:
- what the input basis was
- what structured representation was derived from it

---

## Minimal reproducibility chain

For any materially important result, the repository should ideally support a chain like:

1. snapshot(s)
2. world snapshot(s), where relevant
3. explicit hypotheses
4. scenario
5. agents and models
6. run manifest
7. result
8. validation artifacts
9. report

This ADR does not say every case must be maximally heavy.  
It says the reproducibility core should begin with snapshots and run manifests.

---

## Materiality rule

This ADR is intentionally scoped to materially important work.

Not every trivial exploratory action requires full formalization.

However, once a run or output becomes any of the following:

- report-supporting
- comparison-relevant
- historically meaningful
- validation-relevant
- reused by others
- a stable downstream dependency

then snapshot and run-manifest discipline becomes required.

This preserves flexibility for exploration without weakening canonical reproducibility.

---

## Relationship to human exploratory work

This ADR is consistent with the distinction established in ADR-002.

Exploratory work may occur without full formalization.

But the moment an exploratory run or input state becomes canonically important, it should be promoted into:

- explicit snapshot form
- explicit run-manifest form

This keeps the reproducibility core aligned with the canonical layer.

---

## Trade-offs

This decision has costs.

### Cost 1: more artifact maintenance

Researchers must create and manage snapshots and manifests rather than relying on informal memory or local state.

### Cost 2: more explicit promotion work

Exploratory runs that become important will need formalization.

### Cost 3: some duplication

Information may appear in:
- snapshot metadata
- run manifests
- registries
- downstream reports

These costs are accepted because they produce major gains in:
- reproducibility
- comparability
- auditability
- report integrity
- historical recoverability

---

## Practical implications

This ADR implies several structural directions for the repository.

### Snapshots

The repository should support explicit snapshot artifacts, likely under:
- `data/snapshots/`

### Run manifests

The repository should support explicit run manifests, likely under:
- `simulations/manifests/`

### Registries

The repository should eventually track:
- snapshots
- runs
- results
- reports

through registries.

### Reports

Reports should be expected to reference runs, and thereby indirectly the snapshot state.

### Validation

Validation and evaluation should be able to target:
- snapshots
- run manifests
- run-to-result linkage
- report-to-run linkage

---

## Review rule

A useful architectural review question is:

> Could a careful reviewer reconstruct the governed input basis and the concrete execution context of this result without relying on memory, local machine state, or guesswork?

If the answer is no, then the reproducibility core is incomplete.

---

## Compatibility with lightweight implementation

This ADR does **not** require a heavy system from the beginning.

A lightweight first implementation could still satisfy this ADR using:
- simple YAML snapshots
- simple YAML run manifests
- explicit IDs
- basic refs in results and reports

The architectural requirement is explicitness, not immediate complexity.

---

## Non-goals of this decision

This decision does **not** yet define:

- exact snapshot schema
- exact run-manifest schema
- hashing strategy
- immutability mechanism
- orchestration tooling
- storage backend
- automation level
- how many snapshots are ideal in practice

These may be decided later.

This ADR defines the reproducibility core, not the full technical implementation.

---

## Relation to earlier ADRs

This ADR builds directly on:

### ADR-001

Invest-GT is an artifact-governed, constraint-bound pipeline repository.

### ADR-002

Human exploratory layers must remain distinct from canonical repository layers.

ADR-003 adds:

- snapshots as the governed input freeze layer
- run manifests as the governed execution-binding layer

Together these decisions make the repository's reproducibility logic explicit.

---

## Summary

Invest-GT will treat snapshots and run manifests as the reproducibility core of the repository.

This means:

- snapshots preserve governed input state
- run manifests preserve governed execution context
- results should depend on runs
- report-supporting or otherwise important runs should depend on explicit snapshots
- reports should remain traceable through this chain

This decision is foundational for making the repository auditable, comparable, and historically reconstructable.
