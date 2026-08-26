# Contract: STOP

**Status:** Normative · **Version:** 1.0

---

## Scope

This contract defines **STOP** as a structural outcome of the framework.

STOP is the explicit refusal to proceed when admissibility cannot be
established. It is recorded, not bypassed, and it is not failure.

---

## What STOP is

STOP is a terminal state of an artifact (state, gap, intervention,
evaluation) which records that:

- a contract obligation could not be met,
- a structural prerequisite was absent,
- a contradiction was present that could not be resolved within the
  framework,

and, as a consequence, no further admissible transition exists for
that artifact under current conditions.

---

## What STOP is not

- STOP is **not** an error condition that should be handled silently.
- STOP is **not** an evaluation of the learner.
- STOP is **not** a permanent verdict; conditions may change.
- STOP is **not** a fallback for ambiguity; specific STOP reasons are required.

---

## Obligations

A STOP record MUST contain:

1. The artifact identifier that was STOP'ed.
2. The contract under which the STOP was raised.
3. A specific STOP reason, drawn from the contract's enumerated reasons.
4. A timestamp.
5. A reference to the prior state, so the history is reconstructible.

A STOP MUST NOT:

- be raised without a contract reference,
- use a generic reason where a specific one is available,
- be cleared silently; clearing requires a new admissibility record
  that explicitly references the STOP.

---

## STOP across artifact types

Each contract enumerates its own STOP reasons.
A non-exhaustive structural overview:

| Artifact | Typical STOP reasons |
|---|---|
| Learner State | malformed goal context, unresolved contradictions |
| Gap | referenced state STOP'ed, unreachable target |
| Intervention | pre-condition failed, post-condition unobservable |
| Evaluation | probe outside scale, contradictory observation unresolved |

---

## STOP and progress

A STOP'ed artifact does not block other artifacts unless they
structurally depend on it.

A learner whose state has been STOP'ed for one goal context may
still operate under a different goal context, provided the
contradiction is not present there.

This is a deliberate property:
STOP is local to where admissibility failed, not global to the learner.

---

## Recovery from STOP

There is no automatic recovery from STOP.

A STOP may be cleared only by:

- producing a new artifact (state, gap, intervention) under explicit
  declaration that the prior STOP has been considered,
- recording the consideration in the new artifact,
- proceeding under the new artifact, not the STOP'ed one.

The original STOP is preserved in the history.

---

## Why STOP is first-class

A framework that cannot refuse to act has no boundaries.
A framework with no boundaries cannot make commitments about what
it will not do.

STOP is the structural mechanism by which the framework keeps its
commitments operationally visible.

Where this mechanism is absent, the framework has, in practice,
no contract.
