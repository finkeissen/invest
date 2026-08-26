# learn

A structural framework for **learning as state management** —
gaps, interventions, and dimension shifts as first-class artifacts.

---

## Status

This repository is a **public, conceptual** description of the framework.

It defines:
- what the system is and what it claims,
- which structural concepts are admissible,
- which contracts external implementations are expected to honour,
- which boundaries the system enforces.

It does **not** contain:
- runtime systems,
- operational implementations,
- agent prompts in deployable form,
- routing or orchestration logic,
- curriculum data, evaluation datasets, or learner data.

Reading this repository should make the **idea** clear.
It does not, by design, enable direct reproduction.

---

## In one sentence

`learn` treats knowledge not as content to be consumed,
but as a **state to be managed** — with explicit gaps,
declared interventions, and observable dimension shifts.

---

## What this is

Most learning systems optimize for content delivery and recall.
This framework optimizes for **structural transparency** of the learner state.

A learner state is not a score.
It is a record of:
- what is known and to what depth (dimension shift level),
- where the gaps are (relative to a declared target),
- which interventions have been attempted, with what observable effect,
- where the system refuses to proceed (STOP), and why.

The framework is content-agnostic.
It does not prescribe what to learn.
It structures the act of learning so that it remains auditable.

---

## What this is not

- Not a tutoring product
- Not a curriculum
- Not a prediction engine for grades or outcomes
- Not a substitute for teachers, mentors, or institutions
- Not a model of cognition
- Not a worldview

The framework supports learners and educators.
It does not replace them, and it does not decide what learning is *for*.

---

## Core concepts

The framework rests on five concepts.
Each is defined as a contract, not as an algorithm.

1. **Learner State** — a structured snapshot of what a learner knows,
   at what depth, relative to declared goals.

2. **Gap** — a declared distance between current state and target state,
   on a specific concept and dimension shift level.

3. **Dimension Shift** — a discrete, ordered scale of understanding depth,
   from recall to isomorphic transfer across domains.

4. **Intervention** — a declared action intended to close a gap,
   with explicit pre- and post-conditions.

5. **STOP** — an explicit refusal to proceed, when admissibility
   conditions cannot be met. STOP is not failure; it is boundary
   enforcement.

Each concept has a contract under [`requirements/`](requirements/)
and a structural schema under [`schema/`](schema/).

---

## Pipeline (structural)

The learning pipeline is structurally analogous to research pipelines
that separate hypothesis from evaluation:

```
declared goal
     ↓
gap detection         — identify candidate gaps in learner state
     ↓
intervention          — declare and apply a targeted action
     ↓
dimension-shift eval  — observe whether depth has changed
     ↓
state update          — update learner state, or STOP
```

Each stage produces a versioned artifact.
Each transition is auditable.
Each STOP is recorded, not bypassed.

Operational realisation of this pipeline is **out of scope** for this repository.

---

## Repository structure

```
learn/
├── README.md                ← this file
├── VALUES.md                ← declared external values (non-derived)
├── GLOSSARY.md              ← canonical terminology
├── requirements/            ← public contracts (normative)
├── schema/                  ← structural schemas (machine-readable)
├── lifecycle/               ← state, gap, hypothesis lifecycles
├── compatibility/           ← interfaces to existing exam systems
├── docs/                    ← non-normative explanations
└── 0.legacy/                ← retained earlier material, non-canonical
```

---

## How to read

Recommended reading order:

1. `README.md` (this file)
2. `GLOSSARY.md`
3. `requirements/INDEX.md`
4. `lifecycle/learner_state.md`
5. `docs/why-state-not-content.md`

Reading source files in `schema/` without the corresponding contract
in `requirements/` may lead to category errors.

---

## Authority model

This repository defines structural commitments.
It does not define implementations.

Authority flows in one direction:

```
contract  →  implementation
```

Implementations may exist elsewhere.
They are expected to:
- consume these contracts,
- declare their conformance,
- not silently reinterpret, weaken, or extend them.

Where a contract is silent, behaviour is **undefined**, not implicit.

---

## Related work

`learn` was developed alongside, and is structurally compatible with,
the architectural principles of the [finkeissen research stack](https://github.com/finkeissen)
(layered separation of legacy, research program, MMS, matrix, hypotheses, predictions).

`learn` is an independent sister project.
It is not part of that stack and does not claim authority within it.
The architectural debt is acknowledged; the responsibility is local.

---

## License

Conceptual content: CC BY-NC 4.0 (non-commercial, attribution).
Schema files: CC BY 4.0.
Commercial use or derivative implementations require a separate agreement.

See [`LICENSE`](LICENSE) for the binding text.

---

## Status of commitments

This repository is conservative in what it publishes.

What is here is intended to be:
- stable in structure,
- explicit about boundaries,
- silent where commitments cannot yet be made.

Where the repository is silent, no commitment exists.
