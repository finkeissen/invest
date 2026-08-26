# Invest-GT

**Invest-GT** is a research repository for modeling how political, geopolitical, and strategic developments can propagate into market-relevant outcomes.

The project combines:
- structured world inputs,
- explicit hypotheses,
- agent-based reasoning,
- modular models,
- and simulation/reporting stages

to study how state action, institutional behavior, strategic conflict, and policy shifts may affect sectors, assets, and allocation regimes.

The repository is organized as a **research pipeline** rather than a monolithic model. Each stage defines:
- what goes in,
- what comes out,
- and what the next stage is allowed to assume.

That design principle is central to the project.

---

## What this repository is

Invest-GT is a framework for exploring questions such as:

- How do sanctions change sector-level capital allocation?
- How does election uncertainty propagate into policy-sensitive volatility?
- How do industrial policy moves reshape supply-chain-adjacent repricing before macro data catches up?
- How should strategic and geopolitical developments be represented as structured, testable inputs rather than narrative-only commentary?

The repository is intended as a **research and modeling environment**.  
It is not a single predictive model, not a discretionary macro diary, and not a black-box investment engine.

---

## Core idea

The central methodological idea of Invest-GT is:

> **Separate models first. Validate independently. Define interfaces explicitly. Integrate only after each part is legible.**

In practice, this means:

1. define the world and scope clearly,
2. state hypotheses in falsifiable form,
3. specify agents and their incentives,
4. model interactions in bounded modules,
5. run simulations against defined inputs,
6. evaluate outputs against transparent criteria,
7. generate reports that preserve traceability from input to conclusion.

This prevents the repository from collapsing into a single vague meta-model and makes it easier to inspect where assumptions enter the system.

---

## What this repository is not

Invest-GT does **not** aim to do the following:

- provide direct investment advice,
- replace empirical macro research,
- claim deterministic forecasts,
- model the full world at once,
- infer hidden causality from narrative alone,
- treat LLM outputs as inherently valid,
- collapse political interpretation, market reaction, and investment judgment into one opaque step.

The repo is intentionally designed to resist premature totalization.

---

## Repository structure

### Root

- `README.md` — repository overview and orientation
- `PIPELINE.md` — operational description of the staged workflow
- `docs/` — conceptual and methodological documentation
- `pipeline/` — execution-oriented research stages

### `docs/`

The `docs/` directory contains the conceptual backbone of the project.

Typical contents include:
- `overview.md` — project scope and framing
- `architecture.md` — repository logic and module boundaries
- `validation.md` — validation philosophy and testing logic
- `agent-scoring.md` — scoring logic for agent behavior and outputs
- `examples.md` — illustrative scenario flows
- `roadmap.md` — staged development priorities
- `existing-approaches.md` — positioning relative to adjacent approaches
- `pipeline.md` — conceptual description of the pipeline

### `pipeline/`

The `pipeline/` directory contains the staged research workflow.

Current canonical stages:

- `00_inputs/`
- `01_hypotheses/`
- `02_agents/`
- `03_models/`
- `04_runtime/`
- `05_simulations/`
- `06_tests/`
- `07_reports/`

Each stage has its own README and is expected to define:
- purpose,
- inputs,
- outputs,
- interfaces,
- and failure modes.

---

## Pipeline overview

## `00_inputs/`
This stage defines the structured world the rest of the system operates on.

It includes, for example:
- universe definition
- actor taxonomy
- indicator catalog
- event taxonomy
- asset universe
- base assumptions
- snapshot conventions

This is where the project decides what counts as part of the modeled world and what remains explicitly out of scope.

## `01_hypotheses/`
This stage converts broad intuition into testable claims.

A good hypothesis in this repo should:
- connect to defined inputs,
- state a mechanism,
- produce an observable consequence,
- and be falsifiable within simulation or evaluation.

Example:
- sanctions reallocate capital unevenly across allied and non-allied sectors
- election uncertainty raises volatility more strongly in policy-sensitive sectors than in broad aggregates
- industrial policy shifts reprice supply-chain-adjacent assets before lagging macro confirmation

## `02_agents/`
This stage defines the major strategic actors.

Examples may include:
- state actors
- central banks
- regulators
- strategic firms
- sovereign allocators
- institutional investors

The goal is not to create fictional personalities, but to define bounded decision entities with:
- goals,
- constraints,
- information sets,
- action spaces,
- and likely response patterns.

## `03_models/`
This stage specifies how agents, events, and state transitions interact.

Modeling here should stay modular.  
For example:
- event-to-state models
- state-to-market transmission models
- sector sensitivity models
- coalition or bloc interaction models
- policy-reaction models

The aim is composability, not premature completeness.

## `04_runtime/`
This stage handles execution logic.

Possible responsibilities:
- orchestration
- scenario loading
- stage execution order
- interface enforcement
- experiment configuration
- logging and traceability

## `05_simulations/`
This stage runs scenarios through the configured stack.

A simulation should preserve:
- scenario definition,
- active assumptions,
- participating agents,
- model variants,
- outputs,
- and uncertainty markers.

## `06_tests/`
This stage evaluates whether the system behaves coherently.

Testing may include:
- interface validation
- consistency checks
- scenario reproducibility
- baseline comparisons
- agent scoring
- contradiction detection
- regression testing on known scenario classes

## `07_reports/`
This stage converts runs into legible research outputs.

A report should be able to answer:
- what inputs were used,
- which hypothesis was being tested,
- how agents behaved,
- what the model produced,
- and where uncertainty or failure entered the process.

---

## Design principles

### 1. Modularity over totality
The project prefers multiple inspectable components over one grand, opaque architecture.

### 2. Explicit assumptions
Assumptions should be written down, versioned, and challengeable.

### 3. Falsifiability over rhetorical richness
Interesting narratives are not enough.  
A useful hypothesis must expose itself to possible failure.

### 4. Interfaces before integration
Each stage should declare what it consumes and what it emits before downstream complexity is introduced.

### 5. Traceability
A later report should be able to point back to:
- the input state,
- the relevant hypothesis,
- the agent definitions,
- and the model path that generated the result.

### 6. Bounded ambition
The repository should grow through successful narrow cases, not by claiming universal explanatory scope too early.

---

## Validation philosophy

Validation in Invest-GT is not limited to “did the model say something plausible?”

Instead, validation is treated as a multi-layer problem:

- **input validity** — were the inputs well-defined and appropriately scoped?
- **hypothesis validity** — was the claim testable and meaningfully operationalized?
- **agent validity** — did the agent behave consistently with its defined goals and constraints?
- **model validity** — were transitions and outputs coherent given the stated interfaces?
- **report validity** — does the final write-up preserve enough traceability for review?

This repository assumes that a system can fail in useful ways.  
Those failures should remain visible.

---

## Agent scoring

A central open problem in this project is evaluating whether an agent “played well.”

Invest-GT treats agent evaluation as a structured scoring question rather than a vibe check.

Possible scoring dimensions include:
- internal consistency
- strategic coherence
- action-to-information fit
- goal alignment
- responsiveness to constraints
- scenario appropriateness
- non-contradiction across turns
- performance against defined baselines

The scoring layer exists to prevent “plausible language” from being mistaken for strategic adequacy.

---

## Working style

The repository is intended to be built incrementally.

Recommended progression:

1. stabilize `00_inputs`
2. formulate a small number of strong hypotheses
3. define only the agents required for those hypotheses
4. build minimal models that allow a first end-to-end run
5. test and score behavior before broadening scope
6. expand coverage only after a narrow loop works

In other words:
**do not scale the architecture faster than the method can validate it.**

---

## Suggested near-term development path

The next meaningful milestones are:

### Milestone 1 — Inputs are stable
- finalize coverage
- finalize actor and event taxonomy
- define first canonical snapshots

### Milestone 2 — Hypotheses are load-bearing
- develop 2–3 core falsifiable hypotheses
- connect each one to explicit inputs and observable outputs

### Milestone 3 — First operational agents
- define a minimal set of agents tied to those hypotheses
- avoid broad agent universes too early

### Milestone 4 — First end-to-end run
- one scenario
- one hypothesis set
- a small number of agents
- one report artifact

### Milestone 5 — Scoring and regression
- create a repeatable evaluation method
- compare model/agent behavior across runs

---

## Who this repository is for

This repo is primarily for:
- research-oriented builders
- macro/geopolitical analysts with modeling interests
- agent-simulation designers
- experiment-driven strategy researchers
- teams exploring structured reasoning under uncertainty

It is especially useful for people who want to bridge:
- geopolitical analysis,
- structured simulation,
- and investment-relevant interpretation

without collapsing them into one undocumented step.

---

## Current status

Invest-GT is currently in an early but structurally serious phase.

What is already present:
- a clear architectural split between concept and execution
- a numbered pipeline structure
- a strong `00_inputs` layer
- an emerging hypothesis layer
- an explicit concern for validation and scoring

What remains to be developed:
- richer `01_hypotheses`
- concrete `02_agents`
- minimal executable models
- runtime conventions
- simulation examples
- robust tests and scoring workflows

This is a research protocol becoming a system.

---

## Naming

The canonical project name is:

# **Invest-GT**

Legacy naming variants should be treated as deprecated and removed from active repository surfaces.

---

## Contribution logic

When adding new material, prefer the following order of questions:

1. Which stage does this belong to?
2. What are its inputs?
3. What are its outputs?
4. What assumptions does it add?
5. How could it fail?
6. How will a downstream stage consume it?

If those questions cannot be answered yet, the contribution is probably too early.

---

## Guiding sentence

> Build a system that can explain how it moved from political structure to investment-relevant interpretation — and can show where that explanation may be wrong.

---


