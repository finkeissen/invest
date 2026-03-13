# ADR-006: Registries as the Governance Layer over Canonical Artifacts

## Status

Accepted

---

## Date

2026-03-12

---

## Context

Invest-GT is being developed as an artifact-governed, constraint-bound pipeline repository.

Earlier architectural decisions established that:

- the repository's meaning should live in canonical artifacts rather than hidden implementation state
- human exploratory layers must remain distinct from canonical repository layers
- snapshots and run manifests form the reproducibility core for materially important work
- validation and evaluation are first-class layers
- configuration must remain subordinate to canonical artifacts

These decisions make artifact governance central.

However, once a repository contains multiple artifacts of the same family, another structural problem appears.

Even if artifacts are individually well defined, the repository can still become hard to govern if it lacks an explicit overview layer that answers questions such as:

- which artifacts of this type currently exist?
- which one is active?
- which one is superseded?
- where is the canonical version?
- what depends on what?
- which artifacts are safe to use downstream?
- which ones are draft, invalidated, rejected, or archived?

Without such a layer, governance tends to fragment across:

- filenames
- folder placement
- local memory
- implicit convention
- comments in documents
- ad hoc links in reports or manifests

This creates several predictable failure modes:

- multiple hypotheses exist, but no one knows which one is active
- old scenarios remain in practical use because supersession is invisible
- runs reference artifacts informally rather than canonically
- reports depend on objects whose status is unclear
- artifact history becomes hard to inspect across time
- the repository contains explicit artifacts, but not explicit governance of artifact populations

A clear architectural decision is therefore needed:

How should the repository govern canonical artifacts across families and over time?

---

## Decision

Invest-GT will treat **registries** as the **governance layer over canonical artifacts**.

Registries will function as structured index and lifecycle-control surfaces for artifact families.

The core rule is:

> no important artifact family should rely only on folder presence or filename convention for governance visibility

This means:

1. canonical artifacts remain the primary meaning-bearing objects
2. registries provide the canonical governance overview across those artifacts
3. registries make status, identity, supersession, and dependency visible at the family level
4. downstream work may depend on artifacts, but governance should consult registries to determine which artifacts are current, active, rejected, deprecated, or archived
5. registries are not optional convenience indexes; they are part of repository control

The repository will therefore distinguish between:

- the artifact itself
- the artifact's local metadata
- the registry view that governs the artifact family as a whole

---

## Interpretation

This decision does **not** mean that registries replace artifacts.

Artifacts remain the canonical meaning-bearing units.

Registries exist so that the repository can govern artifacts collectively rather than only one file at a time.

A useful distinction is:

### Artifact

Answers:

> What is this object?

### Registry

Answers:

> What is the status of this object relative to other objects of the same family, and how should the repository treat it?

The artifact contains the substantive object.
The registry contains the governance overview.

Both are necessary.

---

## Why registries are necessary

Artifact-governed repositories often fail not because artifacts are missing, but because artifact populations are under-governed.

For example:

- a strong hypothesis may exist, but there is no visible record that it superseded an older one
- a model may be deprecated, but runs still use it because no registry shows that status clearly
- a report may cite a scenario by filename even though a newer active scenario exists
- a run may use a draft artifact because folder browsing made it look current

Registries solve this class of problem by making family-level governance explicit.

They allow the repository to answer not only:

- what exists?

but also:

- what currently counts?
- what should not be used?
- what replaced what?
- what remains only draft?
- what is still historically important but no longer active?

---

## Consequences

### 1. Important artifact families must have registries

The repository should not treat all artifact families as a flat file collection.

Important families should eventually have explicit registries, especially:

- snapshots or world snapshots
- hypotheses
- scenarios
- agents
- models
- runs
- results
- reports
- validation records
- datasets or source bundles where materially relevant

### 2. Registries become the canonical governance view

When there is ambiguity between:

- a filename
- an old local note
- a stale reference in a report
- a remembered convention
- a registry entry

then the registry should normally be treated as the canonical governance view.

This does not replace the artifact content.
It determines the artifact's governance standing.

### 3. Status becomes visible across artifact families

Registries make lifecycle states visible at a level where the repository can actually govern usage.

Examples include:

- draft
- active
- validated
- deprecated
- superseded
- rejected
- invalidated
- archived

Without registries, these states often remain too implicit.

### 4. Supersession and dependency become inspectable

Registries should help make visible:

- what supersedes what
- what depends on what
- what is active for downstream use
- what remains historically retained but not current

This is essential for auditability and controlled evolution.

### 5. Runs and reports become easier to govern

Runs and reports often depend on many upstream artifacts.

Registries make it easier to check whether those dependencies are:

- active
- deprecated
- draft only
- invalidated
- superseded

This reduces hidden lifecycle mistakes.

---

## What this decision rejects

### Rejected alternative 1: folder structure is sufficient governance

This was rejected because folder placement alone cannot reliably communicate:

- active vs deprecated
- superseded vs archived
- dependency visibility
- family-level overview
- lifecycle state across time

### Rejected alternative 2: artifact-local metadata is enough

This was rejected because artifact-local metadata does not automatically provide a family-level governance view.

A repository still needs a place to ask:

- what are all the active hypotheses?
- which scenario is current?
- which models are approved for which uses?

### Rejected alternative 3: reports and manifests can serve as the governance layer

This was rejected because reports and manifests are downstream artifacts.
They may reference artifacts, but they are not the right place to manage artifact-family lifecycle state.

### Rejected alternative 4: local memory and convention can carry the difference

This was rejected because it makes governance dependent on people remembering implicit rules rather than on inspectable repository structure.

---

## Registry role relative to artifacts

This ADR depends on keeping a strict distinction between:

### Artifact content

The substantive object itself.

Examples:
- the full hypothesis
- the full scenario
- the full model spec
- the full report

### Registry entry

The governance representation of that object within its family.

Examples:
- artifact ID
- status
- version
- canonical ref
- supersedes / superseded_by
- dependency refs
- timestamps

A registry entry should not try to reproduce the entire artifact.
It should carry enough information to govern the artifact responsibly.

---

## Registry role relative to IDs and versioning

Registries build directly on stable IDs and version logic.

The repository has already committed to explicit identity and lifecycle rules for canonical artifacts.

Registries are the place where those rules become inspectable at scale.

That means registry entries should normally surface information such as:

- artifact ID
- artifact type
- current version
- current status
- canonical reference
- supersession links
- dependency links

Without IDs and status logic, registries would be weak.
Without registries, IDs and status logic would remain too scattered.

The two layers are complementary.

---

## Registry role relative to validation and evaluation

Registries should make it easier to see whether artifacts have validation relevance or validation outcomes attached.

For example:

- whether a model is validated
- whether a report was invalidated
- whether a hypothesis remains in review
- whether a result is only accepted for exploratory use

This does **not** mean registries replace validation records.

It means registries should surface enough state to make lifecycle and review consequences visible.

A useful rule is:

> if validation or evaluation materially changes artifact standing, the registry should reflect that change

---

## Registry role relative to snapshots and run manifests

Registries do not replace the reproducibility core established in ADR-003.

Instead, they help govern the objects that reproducibility depends on.

For example:

- the snapshot registry helps show which snapshots are active, partial, stale, or archived
- the run registry helps show which runs completed, failed, or remain exploratory
- the model registry helps show whether a run depended on an active or deprecated model

This makes registries especially useful during:

- run review
- report review
- historical comparison
- artifact supersession
- audit and debugging

---

## Family-level governance principle

Each important artifact family should eventually have a clearly interpretable governance surface.

This does not mean all registries must be equally complex from the start.

But it does mean that artifact families should not remain permanently under-governed.

A practical principle is:

> as soon as an artifact family contains enough objects that status, supersession, or dependency become nontrivial, it needs a registry

This keeps registry introduction proportional to repository maturity.

---

## Recommended registry families

This ADR does not freeze the final registry implementation, but it strongly suggests at least the following registry families over time:

- snapshots or world snapshots
- hypotheses
- scenarios
- agents
- models
- runs
- results
- reports
- validations
- datasets or source packages

These are the families most likely to require visible lifecycle control.

---

## Recommended minimal registry entry logic

A registry entry should make it possible to answer questions such as:

- What is the artifact's stable ID?
- What is its title?
- What is its current status?
- What version is current?
- Where is the canonical artifact?
- What supersedes it or what does it supersede?
- What key dependencies matter?
- Is it safe for downstream active use?

The exact field schema may be refined later, but governance visibility should not be deferred indefinitely.

---

## Registry update rule

A meaningful artifact lifecycle change should normally trigger a corresponding registry update.

Examples include:

- artifact creation
- activation
- validation-linked promotion
- deprecation
- supersession
- invalidation
- archival
- rejection

A useful rule is:

> no major lifecycle change without registry visibility

This helps prevent hidden state drift.

---

## Relation to human exploratory layers

This ADR is consistent with ADR-002.

Registries govern canonical artifacts.
They are not intended to track every rough note, local scratch file, or notebook fragment.

However, once an object is promoted from the human exploratory layer into canonical repository relevance, it should enter the appropriate registry family if that family is governed.

This helps make promotion visible and keeps canonical artifacts from drifting back into informal ambiguity.

---

## Trade-offs

This decision has costs.

### Cost 1: additional governance maintenance

Registry entries must be created and updated.

### Cost 2: possible duplication

Some metadata appears both in artifacts and in registries.

### Cost 3: pressure toward lifecycle explicitness

Teams must decide when something is active, deprecated, superseded, or archived rather than leaving that implicit.

These costs are accepted because they buy:

- clearer artifact governance
- easier repository navigation
- stronger lifecycle control
- better auditability
- fewer hidden dependencies on memory and convention

---

## Practical implications

This ADR implies several structural directions.

### Dedicated registry layer

The repository should maintain a visible registry layer, likely under:

- `registry/`

### Family-specific registry files

A practical early form may include files such as:

- `registry/hypotheses.yaml`
- `registry/scenarios.yaml`
- `registry/models.yaml`
- `registry/runs.yaml`
- `registry/reports.yaml`

The exact list may evolve.

### Review against registry state

Run review, report review, and artifact promotion should increasingly consult registry state rather than relying only on folder browsing.

### Registry-aware reports and manifests

Reports and manifests should reference canonical artifact IDs that can be resolved against registries.

---

## Review rule

A useful architectural question is:

> if a reviewer wants to know which canonical objects of this family exist, which ones are active, and which ones are no longer safe for normal downstream use, can the repository answer that without relying on memory or folder archaeology?

If the answer is no, the registry layer is too weak.

---

## Compatibility with lightweight implementation

This ADR does **not** require a complex registry system from the beginning.

A lightweight implementation can still satisfy it using:

- one YAML file per important artifact family
- simple entries with IDs, status, version, and canonical refs
- manual updates at first

The architectural requirement is not automation. It is visible governance.

---

## Non-goals of this decision

This decision does **not** yet define:

- exact registry schemas
- automation for registry updates
- synchronization tooling between artifact metadata and registries
- database backends
- user interfaces for browsing registries
- enforcement tooling

These may be decided later.

This ADR defines the governance role of registries, not their final implementation mechanics.

---

## Relation to earlier ADRs

This ADR builds directly on:

- ADR-001: artifact-governed, constraint-bound repository architecture
- ADR-002: distinction between human and canonical layers
- ADR-003: snapshots and run manifests as the reproducibility core
- ADR-004: validation and evaluation as first-class layers
- ADR-005: configuration subordinate to canonical artifacts

ADR-006 adds the family-level governance layer that makes artifact lifecycle and current standing visible across the repository.

---

## Summary

Invest-GT will treat registries as the governance layer over canonical artifacts.

This means:

- artifacts remain the substantive objects
- registries provide the family-level governance view
- status, supersession, and dependency must become visible across artifact families
- important artifact families must not rely only on filenames and folder placement for lifecycle control
- downstream work should be able to consult registry state to know what is current, active, deprecated, rejected, invalidated, or archived

This decision is necessary to make artifact governance visible not only one object at a time, but across the repository as a whole.
