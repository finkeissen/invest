# Contract: Learner State

**Status:** Normative · **Version:** 1.0

---

## Scope

This contract defines the structural obligations of any artifact
that claims to represent a **learner state** within the framework.

This contract does **not** define:
- how learner state is stored,
- how it is computed or inferred,
- how it is presented to a learner,
- how it is shared between systems.

---

## Obligations

A learner state artifact MUST contain:

1. A stable learner identifier, scoped to the system that produced it.
2. A timestamp of capture.
3. A reference to the goal context against which it is measured.
4. A set of concept records, each containing:
   - a concept identifier (scoped to a declared concept space),
   - a current dimension shift level (per `dimension_shift.contract.md`),
   - a confidence qualifier (declared, observed, or inferred).
5. A set of currently active gaps (per `gap.contract.md`).
6. An admissibility status:
   either *admissible*, *under review*, or *STOP* with a recorded reason.

A learner state artifact MUST NOT:

- claim a dimension shift level for a concept without a corresponding
  observation or explicit declaration,
- silently merge contradictory observations,
- represent absence as a low value rather than as absence.

---

## Absence vs. low value

Absence is structural.
A concept the learner has not been observed on is **absent**, not zero.
A concept the learner has explicitly failed at is **observed** at the
relevant dimension shift level, with that observation recorded.

Conflating these is inadmissible.

---

## Update obligations

When a learner state is updated, the prior state MUST be retrievable.
Updates are recorded, not overwritten.
This is structural, not a storage suggestion: any implementation that
cannot reconstruct prior states fails this contract.

---

## STOP conditions

A learner state MUST be marked STOP if:

- contradictory observations cannot be reconciled,
- a goal context is referenced that does not exist or is malformed,
- an observation refers to a dimension shift level outside the declared scale,
- an external system has provided data that violates the schema.

STOP is not failure of the learner.
STOP is failure of admissibility, scoped to the artifact.

---

## Out of scope

The following are deliberately out of scope:

- How dimension shift levels are observed in practice
- How concept records are aggregated for display or summary
- How learner states from multiple systems are reconciled
- Any psychometric interpretation of state values

Implementations may address these.
This contract takes no position.
