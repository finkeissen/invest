# Contract: Dimension Shift

**Status:** Normative · **Version:** 1.0

---

## Scope

This contract defines the **dimension shift scale** used throughout the
framework, and the structural requirements for any probe that claims
to observe a level on this scale.

It does not define:
- specific probe questions,
- domain-specific calibration,
- scoring or aggregation procedures.

These are implementation detail.

---

## The scale

Dimension shift is a **discrete, ordered scale** with six levels.

Each level is defined by what the learner can demonstrate;
not by what they have been taught, and not by what they remember.

| Level | Demonstrable capability |
|---|---|
| 0 | The learner can identify or name the concept on prompt. |
| 1 | The learner can explain the concept in their own terms to a non-expert. |
| 2 | The learner can apply the concept to standard problems within its declared domain. |
| 3 | The learner can apply the concept to novel problems within its declared domain. |
| 4 | The learner can combine the concept with concepts from another domain to address a problem neither domain alone resolves. |
| 5 | The learner can recognise the structural form of the concept in a domain to which it has not been taught. |

Levels are **strictly ordered**: a learner at level *n* is presumed
to satisfy levels *0..n-1*, until evidence to the contrary is recorded.

A level is held only when **observable evidence** exists for it.
Self-report alone establishes level 0; not above.

---

## Probe obligations

A probe is a structured prompt that elicits evidence of a specific level.

A probe MUST declare:

1. The level it targets.
2. The concept it tests.
3. The structural form of the expected response (not its content).
4. A clear failure condition: what response would *not* establish the level.

A probe MUST NOT:

- target multiple levels simultaneously without recording which level
  the response established,
- substitute confidence for capability,
- use response speed or fluency as evidence of a level above what
  the response content establishes.

The framework specifies the **structural form** of probes only.
The concrete content of probes — questions, scenarios, exemplars — is
operational and out of scope for this repository.

---

## Calibration

Calibration of probes against domains, exam systems, or learner
populations is the responsibility of the implementation.

This contract requires only that calibration, where performed, be:

- documented,
- reproducible from the documentation,
- subject to the same versioning obligations as the rest of the
  implementation.

The framework takes no position on calibration outcomes.

---

## STOP conditions

Observation of dimension shift MUST trigger STOP if:

- a probe response establishes a level that contradicts a prior,
  unfalsified observation, and the contradiction cannot be resolved
  by recording both as the most recent state,
- a probe is administered for a concept not present in the active
  concept space,
- a probe targets a level above the highest level for which the
  framework has declared a structural definition (i.e. above level 5).

---

## Why six levels

The scale stops at level 5 because:
- below level 0 is structural absence (no observation), not a level,
- above level 5 the structural form (recognition across untaught
  domains) cannot be probed without changing what is being tested.

Extension of the scale would require an explicit contract change.
