# ADR-014: Failures, Invalidations, and Rejections Must Remain Visible

## Status

Accepted

---

## Date

2026-03-13

---

## Context

Repositories often handle success more explicitly than failure.

Yet in a constraint-bound research and simulation architecture, failure states are not noise. They are essential information.

Examples include:

- rejected hypotheses
- invalidated models
- failed runs
- partial outputs
- broken provenance
- scenario contradictions
- report overreach identified after review

If these states are hidden, overwritten, or normalized away, the repository loses:

- epistemic honesty
- auditability
- learning value
- correct lifecycle governance
- the ability to distinguish “not yet admitted” from “once stood, now broken”

A clear architectural decision is therefore required.

---

## Decision

In Invest-GT, **failures, invalidations, rejections, and partial states must remain explicit and governable rather than being hidden, overwritten, or rhetorically normalized away**.

The core rule is:

> a broken artifact path is still meaningful repository state and must remain representable as such

---

## Interpretation

This ADR applies across the repository, including:

- inputs
- snapshots
- hypotheses
- scenarios
- models
- runs
- results
- reports
- validation records

It means the repository should preserve distinctions such as:

- rejected vs invalidated
- failed vs cancelled
- partial vs completed
- caveated vs strong
- archived vs active

These are not cosmetic labels. They are part of the epistemic record.

---

## Consequences

### 1. Failure becomes a first-class state

A failed run should remain visible as failed.

### 2. Invalidated artifacts remain historically meaningful

The repository should not erase them as if they never mattered.

### 3. Rejection remains distinct from invalidation

A claim that never passed is different from one that later broke.

### 4. Reports must not hide upstream breakage

If supporting artifacts are invalidated materially, report standing must be reconsidered visibly.

---

## What this decision rejects

### Rejected alternative 1: overwrite bad states with newer good states

Rejected because history and learning disappear.

### Rejected alternative 2: treat failure as purely technical noise

Rejected because many failures are conceptually informative.

### Rejected alternative 3: rhetorical smoothing in reports

Rejected because communicative neatness must not erase structural weakness.

---

## Practical implications

This ADR supports:

- visible status vocabularies
- failure notes in run manifests
- invalidation records
- retention of rejected artifacts where useful
- report invalidation or downgrade when upstream support breaks materially

---

## Relation to earlier ADRs

This ADR builds especially on:

- ADR-004
- ADR-008
- ADR-010

---

## Summary

In Invest-GT, failure is not something to hide.

Broken, rejected, invalidated, or partial states are part of the governed epistemic record and must remain visible.
