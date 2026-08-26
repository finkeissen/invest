# The Pipeline

A non-normative description of how the framework's artifacts flow
through a typical learning interaction.

For obligations and admissibility rules, see `requirements/`.

---

## Overview

```
goal context
     │
     ▼
learner state  ──────────────────────────────────┐
     │                                            │
     ▼                                            │
gap detection                                     │
     │                                            │
     ▼                                            │
intervention proposed                             │
     │                                            │
     ▼                                            │
intervention applied                              │
     │                                            │
     ▼                                            │
evaluation (probe, observation, external)         │
     │                                            │
     ▼                                            │
admissibility check                               │
     │                                            │
     ├── admissible ───→ updated learner state ───┘
     │
     └── inadmissible ──→ STOP (recorded)
```

Each transition is recorded.
No transition is silent.
STOP is not the absence of a record; it is a specific record.

---

## Stage notes

### Goal context

A goal context enters from outside the framework.
The framework does not generate goals.
Goals may be self-declared by the learner, derived from an external
authority (an exam framework, a curriculum), or composed of both.

If no admissible goal context is present, no gap can be declared.
This is intentional: gaps are always relative to a target.

### Gap detection

Gaps may be detected by declaration (the learner names one), by
observation (an interaction surfaces one), or by derivation (a
prerequisite of another gap).
The mechanism is recorded. The mechanism does not change the gap's
admissibility status.

### Intervention proposed → applied

A proposal is not yet an action.
Between proposal and application, admissibility may be re-checked.
An admissible proposal may be withdrawn before application without
generating STOP.

### Evaluation

Evaluation is the moment the framework learns whether an intervention
did what it claimed.
Evaluation outcomes are recorded regardless of result.
A negative evaluation does not cause STOP. It updates the gap.

### Admissibility check

This is where contracts are enforced.
An update that violates any contract is STOP'ed.
The prior state remains the most recent admissible state.

---

## What the pipeline does not include

- Adaptive routing of learners between interventions
- Real-time tutoring loops
- Conversation or session orchestration
- Aggregation across many learners

These are operational concerns.
They sit outside this repository.

---

## Why an explicit pipeline at all

Without an explicit pipeline, transitions happen as side effects:
the learner answers, something updates somewhere, the next prompt
appears. There is no record of what was inferred, why, or by which
authority.

With an explicit pipeline, every transition is traceable to an
admissibility decision under a contract.
The cost is structural overhead. The benefit is that the system's
behaviour can be inspected, criticised, and corrected.

The framework regards this trade-off as non-negotiable.
