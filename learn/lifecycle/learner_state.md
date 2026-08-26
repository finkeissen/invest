# Lifecycle: Learner State

Non-normative description of how a learner state moves through the
framework over time.

For obligations, see `requirements/learner_state.contract.md`.

---

## Initial state

A learner state begins with a declaration:

- a learner identifier,
- a goal context,
- an empty or initially-populated set of concept records.

A state with no concept records is admissible, but limits which
gaps can be declared against it.

---

## Update as evidence accumulates

When a probe, an evaluation, or an external observation produces
evidence about the learner's understanding of a concept:

```
prior state  →  observation  →  candidate update  →  admissibility check  →  new state
```

Admissibility checks may produce:
- *admissible*: the new state is recorded,
- *under review*: the candidate is held pending resolution,
- *STOP*: the candidate is recorded as STOP and the prior state
  remains the most recent admissible state.

A STOP'ed candidate does not invalidate its prior.

---

## Branching across goal contexts

A learner may operate against more than one goal context simultaneously.
Each goal context has its own state stream.

Branching is structural, not psychological:
the same concept may have different relevance, different target
levels, and different gaps in different goal contexts.

The framework records this; it does not collapse it.

---

## Retirement

A learner state stream may be retired when:
- the goal context is declared complete or abandoned by the learner,
- the goal context expires (e.g. an exam date passes).

Retired streams remain retrievable.
They are not deleted.

---

## What this lifecycle does not address

- How the goal context is constructed
- How concept records are sourced
- Who has authority to update a state
- How states are presented to the learner

Implementations make these choices.
The framework is silent on them.
