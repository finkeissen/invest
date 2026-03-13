# ADR-012: Core Artifact Families Must Not Collapse into Each Other

## Status

Accepted

---

## Date

2026-03-13

---

## Context

In repositories that mix research, modeling, and simulation, one of the most common structural drifts is semantic collapse between artifact families.

Typical examples include:

- a hypothesis used as if it were a scenario
- a scenario used as if it were a run
- a model used as if it were an agent
- a result used as if it were a report
- a report treated as if it were source evidence

Invest-GT explicitly depends on keeping these boundaries legible, because each artifact family serves a different role in the pipeline.

A dedicated architectural decision is therefore needed.

---

## Decision

In Invest-GT, **core artifact families must remain structurally distinct and must not collapse into each other through convenience, naming shortcuts, or implementation shortcuts**.

The core rule is:

> if two artifact families answer different questions in the pipeline, they must remain distinct in architecture and governance

This applies especially to:

- snapshot vs world snapshot
- hypothesis vs scenario
- agent vs model
- run vs result
- result vs report
- report vs evidence layer

---

## Interpretation

The purpose of this ADR is not taxonomic purity for its own sake.

It exists because artifact families become unmanageable when they start silently doing each other’s jobs.

That causes:

- hidden assumptions
- broken contracts
- weak validation
- report overreach
- poor reproducibility
- semantic drift in discussions and code

Distinct artifact families make the pipeline intelligible.

---

## Consequences

### 1. Artifact definitions matter operationally

The canonical definitions are not just documentation. They guide architecture.

### 2. Contracts become easier to state

Stage boundaries are clearer when artifact roles are not blurred.

### 3. Validation becomes sharper

You can only validate something well if you know what kind of object it is.

### 4. Reporting becomes safer

Results remain outputs. Reports remain interpretation.

---

## What this decision rejects

### Rejected alternative 1: convenience collapse

Rejected because “it is close enough” destroys boundary clarity over time.

### Rejected alternative 2: code-first semantic merging

Rejected because implementation shortcuts often erase important conceptual distinctions.

### Rejected alternative 3: report-driven semantic collapse

Rejected because interpretive output must not redefine upstream artifact types retroactively.

---

## Practical implications

This ADR supports:

- separate schemas per major artifact family
- separate registry families
- separate validation logic by artifact type
- explicit contract mapping between types

---

## Relation to earlier ADRs

This ADR depends on and sharpens:

- ADR-001
- ADR-007
- ADR-008

---

## Summary

Invest-GT depends on distinct artifact families doing distinct jobs.

That distinction is architectural, not optional.
