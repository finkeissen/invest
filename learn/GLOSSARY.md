# Glossary

Canonical terminology for this repository.

Where a term in this glossary differs from common usage, the glossary
takes precedence within the framework.

---

## Admissibility

A property of an artifact (state, gap, intervention, claim).
An artifact is admissible if its contract is satisfied and no
boundary condition is violated. Inadmissible artifacts trigger STOP.

## Artifact

Any structured object produced or consumed by the framework:
a learner state snapshot, a gap, an intervention record, an
evaluation, a session manifest.

## Dimension Shift

An ordered, discrete scale describing the depth at which a concept
is understood. The scale ranges from surface recall to transfer
across structurally similar domains. Specific levels are defined
in `requirements/dimension_shift.contract.md`.

## Evaluation

The act of observing, after an intervention, whether the learner
state has changed in the way the intervention predicted.
An evaluation produces a record, not a judgement.

## Gap

A declared distance between a current learner state and a declared
target state, scoped to a concept and a dimension shift level.
A gap is a structured claim, not a deficit attribution.

## Goal

An externally declared target state.
Goals are inputs to the framework, not outputs.
The framework does not derive goals.

## Intervention

A declared action intended to reduce a gap.
An intervention has explicit pre-conditions, an expected effect,
and a post-condition that can be evaluated.

## Learner State

A structured snapshot of what is known, at what depth, by a single
learner, at a specific time, relative to declared goals.

## Probe

A structured prompt designed to elicit observable evidence of the
current dimension shift level for a concept. Probes are described
by their structural form in this repository; concrete probe content
is operational and out of scope.

## Run

A bounded interaction (typically one session) that begins with a
learner state, applies one or more interventions, and ends with
either an updated state or STOP.

## STOP

An explicit refusal to continue a transition, when admissibility
conditions cannot be established.
STOP is recorded, not bypassed.
STOP is not failure.

## Target State

The state a learner has declared (or been declared toward, by an
external authority such as an exam system).
A target is structural, not normative.

---

## Terms intentionally **not** defined here

The following terms appear in some related literature but are
**not part of this framework**:

- *Mastery* — too entangled with assessment regimes
- *Talent* — not operationalisable within these contracts
- *Intelligence* — outside scope
- *Truth* (of a concept) — handled, if at all, outside this framework

Their absence is deliberate.
