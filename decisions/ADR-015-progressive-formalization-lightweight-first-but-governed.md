# ADR-015: Progressive Formalization — Lightweight First, but Governed from the Start

## Status

Accepted

---

## Date

2026-03-13

---

## Context

Invest-GT is still in an early architectural phase.

At this stage, there is a legitimate tension between two risks.

### Risk 1: under-structuring

If the repository stays too loose for too long, the later implementation phase will drift around hidden assumptions, weak artifact identity, and unclear execution semantics.

### Risk 2: premature overengineering

If the repository tries to implement every schema, automation layer, and governance mechanism at full industrial complexity immediately, it may become slow, brittle, and hard to evolve.

A clear decision is therefore needed about the implementation posture of the architecture.

---

## Decision

Invest-GT will follow a **progressive formalization** approach:

- lightweight in initial implementation mechanics
- strict in conceptual governance from the beginning

The core rule is:

> the repository may start simple in tooling, but it must not start vague in structure

This means:

1. conceptual boundaries should be explicit early
2. governance expectations should be explicit early
3. technical implementation may begin with lightweight mechanisms
4. heavier automation or strict schema enforcement may arrive later
5. simplicity is acceptable; conceptual ambiguity is not

---

## Interpretation

This ADR is a practical implementation posture for the earlier architectural decisions.

It says that the repository does **not** need, on day one:

- a full orchestration engine
- a perfect schema framework
- automated registry synchronization
- a complex database backend
- a heavy internal platform

But it **does** need, from the beginning:

- explicit artifact distinctions
- IDs and lifecycle logic for major artifacts
- visible stage contracts
- snapshot and run-manifest concepts
- visible validation intent
- traceable reporting logic

---

## Consequences

### 1. Simple formats are acceptable early

For example:

- Markdown
- YAML
- lightweight registries
- manual but explicit manifests

These can be sufficient at first.

### 2. Governance comes before automation

The architecture must be conceptually right before it becomes heavily automated.

### 3. Manual steps are acceptable if explicit

Manual curation or manifest creation is acceptable early if it remains visible and governed.

### 4. Hidden shortcuts are not acceptable just because tooling is early

Lack of automation is acceptable.
Lack of structure is not.

---

## What this decision rejects

### Rejected alternative 1: tool-heavy architecture before conceptual stabilization

Rejected because it risks freezing weak abstractions into infrastructure.

### Rejected alternative 2: remain informal until code appears

Rejected because later code would inherit ambiguity.

### Rejected alternative 3: use early-stage status as excuse for hidden state

Rejected because early repository maturity does not justify epistemic drift.

---

## Practical implications

This ADR supports an early repository state where:

- docs define the architecture clearly
- ADRs define major structural choices
- schemas may begin lightweight or partially specified
- registries may begin as simple YAML files
- snapshots and run manifests may be hand-authored initially
- validation may begin as explicit records before automation

That is acceptable, provided the governance logic is already explicit.

---

## Relation to earlier ADRs

ADR-015 acts as the implementation posture for the broader ADR set, especially:

- ADR-001
- ADR-003
- ADR-006
- ADR-007

---

## Summary

Invest-GT should start simple in tooling, but not vague in structure.

The repository will therefore formalize progressively:

- lightweight first
- governed from the start
- heavier automation only after conceptual stability is secured
