# ADR-011: Inputs Are Governed Through Raw, Curated, Canonical, and Snapshot Layers

## Status

Accepted

---

## Date

2026-03-13

---

## Context

Invest-GT depends on input material that is often mixed in quality, temporality, and interpretive structure.

The repository may contain:

- raw source materials
- extracted observations
- curated notes
- cleaned tables
- context packages
- frozen input states for runs

If all of these are collapsed into one undifferentiated “data” layer, several problems emerge:

- provenance becomes blurry
- interpretation enters invisibly
- runs become harder to reproduce
- reviewers cannot see what changed between input states
- raw source, curation, and frozen execution basis become conflated

A structural decision is therefore needed for input layering.

---

## Decision

Invest-GT will govern inputs through four conceptually distinct layers:

1. **raw**
2. **curated**
3. **canonical**
4. **snapshot**

The core rule is:

> no materially important downstream artifact should depend on an input layer whose transformation state is unclear

---

## Interpretation

These layers are not merely storage convenience.

They represent meaningful differences in epistemic and operational status.

### Raw

Closest repository representation of source material.

### Curated

Selected, cleaned, annotated, or grouped material.

### Canonical

Governed input artifacts judged suitable for active downstream use.

### Snapshot

A frozen bounded input state for reproducible downstream work.

Keeping these layers separate helps preserve lineage and interpretability.

---

## Consequences

### 1. Raw is not automatically downstream-ready

Source presence does not equal downstream admissibility.

### 2. Curated remains visibly curated

Human and machine transformation should remain legible.

### 3. Canonical becomes the stable active input layer

Downstream governed artifacts should normally rely on governed canonical inputs or snapshots.

### 4. Snapshots become the reproducibility bridge

Frozen input state should be explicit for important downstream work.

---

## What this decision rejects

### Rejected alternative 1: single undifferentiated data folder

Rejected because it hides transformation state and weakens provenance clarity.

### Rejected alternative 2: current data as sufficient execution basis

Rejected because current state is not a reproducible historical state.

### Rejected alternative 3: raw and interpreted materials mixed without distinction

Rejected because that blurs where interpretation entered the pipeline.

---

## Practical implications

This ADR supports structures such as:

- `data/raw/`
- `data/curated/`
- `data/canonical/`
- `data/snapshots/`

and metadata that preserves lineage between them.

---

## Relation to earlier ADRs

This ADR builds on:

- ADR-003
- ADR-006
- ADR-007

---

## Summary

Inputs in Invest-GT are not one flat layer.

They are governed across raw, curated, canonical, and snapshot states so that provenance, transformation, and reproducibility remain visible.
