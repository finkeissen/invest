# Contract: Gap

**Status:** Normative · **Version:** 1.0

---

## Scope

This contract defines what counts as a **gap** within the framework.

A gap is a structured claim about a learner state.
It is not an evaluation of the learner.
It is not a deficit attribution.

---

## Obligations

A gap MUST be declared with:

1. A stable gap identifier, scoped to the producing system.
2. A reference to a learner state in which the gap is asserted.
3. A concept identifier (the gap is about a specific concept).
4. A current dimension shift level (observed or absent).
5. A target dimension shift level (declared or inherited from goal context).
6. A detection source: how the gap came to be declared.
7. A status: *open*, *closed*, *superseded*, or *STOP*.

A gap MUST NOT:

- claim a dimension shift level the learner state does not record,
- assert distance from a target the learner has not, directly or by
  inheritance, accepted,
- be silently closed without an evaluation record.

---

## Detection sources

The contract recognises three structural categories of detection:

- **declared** — the learner stated the gap themselves
- **observed** — the gap was inferred from a recorded interaction
- **derived** — the gap follows from a structural prerequisite of another gap

How any of these are produced is implementation detail and out of scope.

---

## Closing a gap

A gap may be closed only when:

- an evaluation record exists that observed the target dimension shift level,
- the evaluation references the same concept and learner,
- the evaluation post-dates the most recent intervention against the gap.

Closure without these conditions is inadmissible and triggers STOP.

---

## Superseding a gap

A gap may be marked *superseded* when:

- a structurally broader gap has been declared that subsumes it,
- the goal context has changed such that the target dimension shift
  level is no longer applicable,
- the concept itself has been retired from the active concept space.

Superseded gaps remain retrievable.

---

## STOP conditions

A gap MUST be marked STOP if:

- the referenced learner state has been marked STOP,
- the concept it refers to has been removed from the concept space
  without a supersede record,
- the target dimension shift level cannot be reached under any admissible
  intervention currently declared.

The third condition is structural, not pedagogical:
it concerns whether the system can act, not whether the learner can learn.

---

## Out of scope

- Heuristics for prioritising gaps
- Automatic gap detection from text or audio
- Any claim about the learner's reasons for the gap
- Any claim about the learner's capacity

This contract is silent on all of these.
