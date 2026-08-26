# Contract: Intervention

**Status:** Normative · **Version:** 1.0

---

## Scope

This contract defines what counts as an **intervention** within the framework.

An intervention is a declared action intended to reduce a gap.
Whether it succeeds is observed, not assumed.

This contract does not define:
- what kinds of interventions are pedagogically effective,
- how interventions are selected,
- how they are delivered.

---

## Obligations

An intervention MUST be declared with:

1. A stable intervention identifier.
2. A reference to the gap (or gaps) it addresses.
3. A reference to the learner state at declaration time.
4. A pre-condition: what must be true for the intervention to be
   admissible at all.
5. An expected effect: which dimension shift level the intervention
   is expected to establish, on which concept.
6. A post-condition: how the expected effect would be observed.

An intervention MUST NOT:

- be applied to a gap that does not exist,
- be applied to a closed or superseded gap without re-opening it
  with a recorded reason,
- claim to address gaps it cannot, given its declared scope,
- be evaluated by a probe at a level different from the one it declared.

---

## Lifecycle

An intervention proceeds through declared states:

- **proposed** — declared, not yet applied
- **applied** — the action has been taken
- **evaluated** — a post-condition observation has been recorded
- **closed** — evaluation is complete; the gap is updated accordingly
- **STOP** — admissibility failed at any stage

State transitions are append-only and recorded.

---

## Evaluation

Evaluation of an intervention MUST:

- use a probe that targets the level the intervention claimed,
- record the result regardless of whether it confirms the expected effect,
- update the gap status only as the recorded result warrants.

A failed intervention is **not** a failure of the learner.
It is a failure of the intervention's prediction.
The framework records this distinction.

---

## Composition

Multiple interventions may be active simultaneously across distinct gaps.

Multiple interventions on the **same gap** are admissible only if:
- they are declared as a sequence with a recorded order, or
- they are declared as alternatives with explicit selection criteria.

Concurrent interventions on the same gap without one of these
declarations are inadmissible and trigger STOP.

---

## STOP conditions

An intervention MUST be marked STOP if:

- its pre-condition fails at the time of application,
- the gap it references has been STOP'ed,
- the learner state it references has been STOP'ed,
- it claims an expected effect outside the declared dimension shift scale,
- the post-condition is structurally unobservable.

The last condition is important:
an intervention that cannot in principle be evaluated is inadmissible.

---

## Out of scope

- The catalogue of intervention types
- The pedagogical rationale for any intervention
- Routing logic that selects interventions
- Adaptation logic that modifies interventions during application

These are implementation concerns and are not specified here.
