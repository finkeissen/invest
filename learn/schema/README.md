# Schemas

Machine-readable structural schemas for the framework's artifacts.

These schemas describe **structure only**.
They do not encode operational behaviour.

| Schema | Contract |
|---|---|
| `learner_state.schema.json` | `requirements/learner_state.contract.md` |
| `gap.schema.json` | `requirements/gap.contract.md` |
| `intervention.schema.json` | `requirements/intervention.contract.md` |

A schema is the **form**.
The contract is the **obligation**.
Validation against the schema is necessary but not sufficient for
contract compliance.

---

## What is **not** here

- Concrete examples populated with real concept IDs, real probes, or
  real learner data
- Schemas for evaluations, runs, or session manifests
  (these depend on operational structure and are not yet stable)
- Validation tooling

The absence of these is deliberate.
A reference implementation, if and when published, would carry them.
