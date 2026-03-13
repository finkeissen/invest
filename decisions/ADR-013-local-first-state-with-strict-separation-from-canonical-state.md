# ADR-013: Local-First State with Strict Separation from Canonical State

## Status

Accepted

---

## Date

2026-03-13

---

## Context

Invest-GT is expected to support significant local exploratory work:

- notebooks
- scratch analysis
- temporary curation
- local runtime experiments
- environment-specific execution settings

At the same time, the repository must preserve a canonical governed layer for artifacts, manifests, registries, and reports.

Without a clear architectural boundary between local and canonical state, several problems arise:

- machine-specific state leaks into governed execution meaning
- local overrides become invisible assumptions
- “works on my machine” becomes report-relevant state
- reproducibility weakens
- local convenience silently outruns repository governance

A decision is therefore needed on local-vs-canonical state handling.

---

## Decision

Invest-GT will follow a **local-first but canonical-separated** model.

This means:

1. local exploratory and technical state is allowed and expected
2. local state must remain explicitly separate from canonical repository state
3. local state must not silently determine artifact meaning, governance standing, or report-supporting run interpretation

The core rule is:

> local state may support work, but canonical meaning must never depend on hidden local state

---

## Interpretation

This ADR intentionally allows real local work.

It rejects only one thing: hidden dependence on local state for canonical repository truth.

Examples of legitimate local state:

- caches
- temp outputs
- notebook scratch artifacts
- machine paths
- local experimental notes
- local-only technical overrides

Examples of illegitimate hidden local dependence:

- a report-supporting run whose real config existed only on one machine
- a scenario whose effective version lived only in a notebook
- validation behavior altered by local defaults without manifest visibility

---

## Consequences

### 1. Local config must be separated from canonical config

### 2. Local scratch work must not silently become canonical artifact truth

### 3. Canonical artifacts must remain machine-independent in meaning

### 4. Important runs must surface any materially relevant overrides

---

## What this decision rejects

### Rejected alternative 1: implicit local-state architecture

Rejected because it destroys reproducibility and auditability.

### Rejected alternative 2: banning local work entirely

Rejected because real research requires exploratory local practice.

### Rejected alternative 3: environment settings with conceptual force

Rejected because conceptual meaning belongs in governed artifacts, not hidden machine state.

---

## Practical implications

This ADR supports patterns such as:

- `configs/local/`
- clear `.gitignore` boundaries
- environment-local settings kept out of canonical manifests unless materially relevant
- promotion from local exploratory work into canonical artifact form where needed

---

## Relation to earlier ADRs

This ADR refines:

- ADR-002
- ADR-003
- ADR-005

---

## Summary

Invest-GT allows local-first exploratory work.

But canonical repository meaning must remain explicitly separate from local machine state.
