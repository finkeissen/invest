# ADR-009: Governance Truth Lives in Registries, Status, and Manifests

## Status

Accepted

---

## Date

2026-03-13

---

## Context

Once a repository contains multiple artifacts across time, a recurring structural question appears:

Where does the repository determine what is currently active, deprecated, superseded, rejected, or valid for downstream use?

In weak repositories, this answer becomes fragmented across:

- folder placement
- filenames
- local memory
- comments in documents
- notebook conventions
- implied recency
- “everybody knows” habits

That kind of informal governance quickly becomes unstable in a system with:

- multiple hypothesis versions
- scenario revisions
- reruns
- archived reports
- invalidated artifacts
- competing configs
- historical comparisons

Invest-GT therefore needs a clear rule about where governance truth lives.

---

## Decision

In Invest-GT, **governance truth will live in explicit registries, explicit status fields, and explicit manifests rather than in folder position, naming habits, or tacit memory**.

This means:

1. registries determine visibility across artifact families
2. status fields determine lifecycle standing
3. manifests determine concrete execution binding
4. filenames and folder positions remain organizational aids, not governance authority

The core rule is:

> if an artifact matters enough to govern, its governance state must be explicit and inspectable

---

## Interpretation

This ADR does not mean that every tiny object requires a full governance layer immediately.

It means that major artifacts must not derive their effective status from informal signals such as:

- “it sits in the active folder”
- “this file looks newest”
- “that doc is the one we meant”
- “the notebook from last week is the latest”

Such signals may help orientation, but they are not sufficient as canonical governance truth.

---

## Why this decision is needed

Without it, the repository will drift into ambiguous state handling.

Typical failures include:

### Failure mode 1: active vs deprecated is unclear

A model still exists but no one knows whether it is still preferred.

### Failure mode 2: superseded artifacts remain silently in use

A run or report references something older because there is no visible governance state.

### Failure mode 3: run context becomes unclear

Execution happened, but no manifest clearly binds the chosen artifact set.

### Failure mode 4: archive and invalidation lose meaning

Old artifacts remain present but not governably classified.

This ADR prevents governance-by-accident.

---

## Consequences

### 1. Registries become the governance overview layer

Registries should provide the visible index of major artifact families.

### 2. Status becomes mandatory for major artifacts

Artifacts should carry explicit lifecycle state where relevant.

### 3. Manifests become mandatory for governed execution

Concrete execution should not be reconstructed from scattered hints.

### 4. Folder structure becomes secondary

Folders may suggest organization. They do not settle lifecycle truth.

### 5. Filename recency is not a valid governance mechanism

Names may assist humans, but should not replace IDs, status, or registries.

---

## What this decision rejects

### Rejected alternative 1: folder-based governance

Rejected because folder logic is too weak and too easy to drift.

### Rejected alternative 2: filename-based governance

Rejected because filenames are mutable and too easy to misread.

### Rejected alternative 3: memory-based governance

Rejected because tacit knowledge does not scale and is not auditable.

---

## Practical implications

This ADR supports structures such as:

- `registry/*.yaml`
- explicit status fields in artifacts
- run manifests under `simulations/manifests/`
- report and result references back to governed run IDs

---

## Relation to earlier ADRs

This ADR builds especially on:

- ADR-001
- ADR-003
- ADR-006

It turns the registry/status/manifest triad into the repository’s canonical governance view.

---

## Summary

In Invest-GT, governance truth must be explicit.

For major artifacts, that means:

- registries for visibility
- status for lifecycle standing
- manifests for concrete execution truth
