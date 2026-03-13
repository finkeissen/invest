# ADR-010: Major Artifacts Require Stable IDs, Status, and Supersession Logic

## Status

Accepted

---

## Date

2026-03-13

---

## Context

Invest-GT relies on multiple artifact families that evolve over time.

Examples include:

- hypotheses
- scenarios
- models
- snapshots
- runs
- reports
- validation records

Without stable identity and lifecycle handling, these artifacts become hard to compare, reference, or retire responsibly.

Common weak patterns include:

- talking about “the current scenario” without stable ID
- replacing old files silently
- losing track of what superseded what
- confusing rejection with invalidation
- reusing names while changing underlying meaning

A specific decision is needed on artifact identity and lifecycle handling.

---

## Decision

All **major canonical artifacts in Invest-GT require stable IDs, explicit lifecycle status, and explicit supersession logic where relevant**.

The core rule is:

> if an artifact can be depended on, compared, reviewed, or replaced, it must be identifiable and lifecycle-visible

This means:

1. major artifacts get stable IDs
2. major artifacts carry visible status where relevant
3. replacement is made explicit through supersession rather than silent overwrite
4. rejection and invalidation remain distinct states

---

## Interpretation

Stable identity is not bureaucratic decoration.

It is what makes it possible to answer questions such as:

- Which hypothesis is being referenced?
- Is this the same scenario as before or a new one?
- Which report version is current?
- Was a model deprecated or invalidated?
- What replaced the older artifact?

Without these answers, the repository loses structural clarity.

---

## Consequences

### 1. IDs become canonical

Artifact IDs matter more than filenames.

### 2. Status becomes part of artifact meaning

A draft and an active artifact are not interchangeable.

### 3. Supersession replaces silent replacement

When one artifact meaningfully replaces another, that should remain visible.

### 4. Invalidation remains distinct from rejection

Rejected means not admitted.
Invalidated means previously standing, later broken.

That difference is epistemically important.

---

## What this decision rejects

### Rejected alternative 1: filenames as identity

Rejected because names are too mutable and insufficient for lifecycle governance.

### Rejected alternative 2: overwrite-in-place evolution

Rejected because silent replacement destroys history and comparability.

### Rejected alternative 3: vague lifecycle language

Rejected because “old”, “new”, “better”, and “latest” are not a sufficient governance model.

---

## Practical implications

This ADR supports:

- canonical prefixes like `HYP-`, `SCN-`, `MOD-`, `RUN-`, `RPT-`
- explicit status fields
- explicit supersedes / superseded_by relations where needed
- reportable separation between draft, active, deprecated, superseded, rejected, invalidated, archived

---

## Relation to earlier ADRs

This ADR sharpens the lifecycle side of:

- ADR-001
- ADR-006
- ADR-009

---

## Summary

If an artifact matters, it must be:

- identifiable
- status-visible
- replaceable only explicitly

Stable IDs, status, and supersession are therefore mandatory for major artifacts.
