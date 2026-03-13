# ADR-008: Reports Remain Downstream and Must Not Become the Evidence Layer

## Status

Accepted

---

## Date

2026-03-13

---

## Context

Invest-GT is designed as an artifact-governed, constraint-bound pipeline repository.

Within that architecture, reports are necessary because the repository must eventually produce interpretable outputs for review, comparison, archival use, and bounded decision support.

However, reports are also one of the highest-risk layers in the repository.

The common failure pattern is not that reports fail to exist, but that they become structurally too powerful. When that happens, they begin to function as if they were:

- the primary evidence layer
- the canonical record of what happened
- the substitute for run history
- the substitute for provenance
- the substitute for validation
- the place where uncertainty is quietly compressed away

This is especially dangerous in a repository that deals with:

- uncertain world models
- evolving input states
- hypotheses and scenarios
- simulation outputs that require interpretation
- allocation-relevant implications that can easily be overstated

A clear architectural decision is therefore needed on the status of reports.

---

## Decision

In Invest-GT, **reports will remain downstream interpretive artifacts and must not become the evidence layer**.

This means:

1. reports may summarize, compare, interpret, and communicate
2. reports must remain tied to explicit upstream artifacts
3. reports must not replace provenance, runs, results, validation, or source support
4. reports must not silently upgrade tentative outputs into settled conclusions
5. reports must preserve visible uncertainty, assumptions, and limitations where materially relevant

The core rule is:

> reports may make the artifact chain easier to understand, but they may not replace the artifact chain

---

## Interpretation

A report is legitimate when it helps a reader understand a governed artifact path.

A report becomes structurally weak when it starts to act as if it were the primary truth object of the repository.

The repository therefore distinguishes clearly between:

- evidence and support
- execution history
- validation history
- interpretation
- communication

Reports belong mainly to the last two categories.

---

## Why this decision is needed

Without this decision, reports tend to accumulate hidden architectural power.

Typical failure modes include:

### Failure mode 1: report as implicit source of truth

People stop inspecting snapshots, hypotheses, scenarios, runs, and validation records because the report appears to contain “the answer.”

### Failure mode 2: report as replacement for execution history

A result is cited from a report even though the run manifest behind it is unclear or missing.

### Failure mode 3: report as uncertainty laundering

A fragile result appears stable because the report compresses caveats for readability.

### Failure mode 4: report as post hoc rationalization

A report presents a smooth story that the upstream artifacts do not actually support cleanly.

### Failure mode 5: report as hidden methodological layer

Load-bearing interpretation choices happen in report prose rather than in governed artifacts, contracts, or validation records.

This ADR exists to prevent these patterns.

---

## Consequences

### 1. Reports must reference upstream artifacts

A report should be tied, where relevant, to:

- snapshots
- world snapshots
- hypotheses
- scenarios
- run manifests
- results
- validation records

### 2. Reports cannot stand in for provenance

If a report depends on source-derived claims, the provenance chain must remain recoverable outside the report.

### 3. Reports cannot stand in for runs

A report may summarize a run. It must not replace the run manifest.

### 4. Reports cannot stand in for validation

A report may mention validation outcomes. It must not replace explicit validation records.

### 5. Reports must preserve uncertainty and limitations

The report layer must not erase assumptions, caveats, fragility, or unresolved issues for rhetorical smoothness.

### 6. Reports may be revised, but revision must remain visible

Material changes to reports require explicit revision handling rather than silent rewriting.

---

## What this decision rejects

### Rejected alternative 1: reports as the main repository interface and de facto truth layer

Rejected because it would weaken auditability and hide artifact-chain structure.

### Rejected alternative 2: executive-summary-first architecture

Rejected because high-compression outputs are especially prone to overstatement if they become architecturally primary.

### Rejected alternative 3: reports as acceptable substitutes for missing manifests or weak provenance

Rejected because downstream readability does not repair upstream weakness.

---

## Practical implications

This ADR implies that reports should:

- remain explicitly linked to upstream artifacts
- include assumptions in force where relevant
- include uncertainty and limitation notes where relevant
- avoid language that outruns validation status
- support traceability back to runs and evidence layers

It also implies that the repository should never rely on reports alone to determine:

- what was executed
- what was validated
- which input state was in force
- which hypothesis versions were active

---

## Relation to earlier ADRs

This ADR builds on:

- ADR-001: artifact-governed, constraint-bound pipeline
- ADR-003: snapshots and run manifests as reproducibility core
- ADR-004: validation and evaluation as first-class layers

ADR-008 clarifies that the report layer remains downstream of all of these.

---

## Non-goals of this decision

This ADR does not define:

- report templates
- exact report schema
- publication workflows
- rendering/export format
- audience-specific style guides

It defines report status in the architecture, not full report implementation.

---

## Summary

In Invest-GT, reports remain downstream governed interpretation artifacts.

They may clarify the artifact chain.
They may not replace it.
