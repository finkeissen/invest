# Requirements

This directory contains the **public contracts** of the framework.

Everything in this directory is:
- **public** — readable by anyone with repository access
- **normative** — implementations are expected to comply
- **structural** — defines obligations, not implementations
- **versioned** — changes are explicit and auditable

If a behaviour is not specified here, it is **not guaranteed** by the framework.
Undefined behaviour is **forbidden**, not implicit.

---

## Contracts

| File | Subject |
|---|---|
| `learner_state.contract.md` | Structure and obligations of the learner state |
| `gap.contract.md` | What a gap is and how it must be declared |
| `dimension_shift.contract.md` | The depth scale and admissible probes |
| `intervention.contract.md` | Required form of an intervention |
| `stop.contract.md` | Conditions under which STOP must be raised |
| `agent_roles.contract.md` | Role obligations (without prompt content) |

---

## What is **not** in this directory

- Concrete prompt text or templates
- Routing logic between models or agents
- Specific probe questions or curriculum mappings
- Thresholds, weights, or scoring formulae
- Any operational artifact that would enable direct reproduction

These belong to implementations.
This repository is silent about them by design.

---

## Reading order

1. `learner_state.contract.md`
2. `gap.contract.md`
3. `dimension_shift.contract.md`
4. `intervention.contract.md`
5. `stop.contract.md`
6. `agent_roles.contract.md`

Each contract is short and self-contained.
Contracts reference each other but do not depend on implementation detail.
