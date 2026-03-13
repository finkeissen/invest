# Pipeline Guide

The `pipeline/` directory is the operational backbone of Invest-GT.

Its purpose is to make the full work sequence explicit: from scope and assumptions, through hypotheses and model design, to runtime logic, simulation output, testing, and reporting.

The separation is intentional:

- `docs/` explains concepts, architecture, validation logic, and project positioning
- `decisions/` records architectural and methodological choices
- `pipeline/` shows the execution sequence of the research workflow
- root-level implementation folders hold reusable assets and code

## Recommended sequence

1. `pipeline/00_inputs/`
2. `pipeline/01_hypotheses/`
3. `pipeline/02_agents/`
4. `pipeline/03_models/`
5. `pipeline/04_runtime/`
6. `pipeline/05_simulations/`
7. `pipeline/06_tests/`
8. `pipeline/07_reports/`

## Why the pipeline lives in its own folder

A dedicated pipeline folder keeps three layers separate:

- explanatory documentation
- reusable assets and implementations
- the actual order of work

That separation makes the repository easier to understand, extend, validate, and hand over.

## Pipeline logic

The logic is cumulative.

- **Inputs** define scope, assumptions, events, indicators, and coverage.
- **Hypotheses** convert intuition into explicit claims.
- **Agents** specify decision-making units and their capabilities.
- **Models** formalize mechanisms and interfaces.
- **Runtime** defines orchestration and execution behavior.
- **Simulations** generate structured scenario outputs.
- **Tests** verify consistency, limits, and failure modes.
- **Reports** convert outputs into interpretable conclusions.

Each stage should depend on declared outputs from earlier stages, not on hidden assumptions.

## Naming recommendation

At the repository root, semantic names are preferable. Inside `pipeline/`, numeric prefixes make execution order explicit.

The intended combination is:

- semantic names at the root
- numbered stages inside `pipeline/`

## Multi-level investment view

The pipeline should support at least three analytical levels:

- **person level**
- **group or institution level**
- **state or geopolitical level**

This matters because investment is broader than financial allocation. A person may invest in health, education, time structure, or relationships. A group may invest in trust, coordination, institutional quality, or security. A state may invest in industrial policy, defense, energy security, or legitimacy.

The pipeline should allow these levels to stay distinct before they are aggregated or compared.

## Quality standard for each stage

Every pipeline stage should answer five questions:

1. What is in scope?
2. What is out of scope?
3. What assumptions are being made?
4. What outputs should the next stage be allowed to rely on?
5. How could this stage fail or distort downstream work?

## Current priority

The immediate priority is to make the lower stages strong enough that downstream hypotheses and models do not have to invent hidden assumptions.

In practice, that means:

- strengthening `00_inputs/`
- tightening hypothesis structure in `01_hypotheses/`
- keeping agent and model boundaries explicit
- preserving a path from broad theory to practical use

## Reading note

For a bottom-up review of the repository, read the numbered pipeline stages first and move to the higher-level documentation only afterward.


## Newly required practical inputs

To support life-portfolio construction as well as geopolitical analysis, `pipeline/00_inputs/` should explicitly accommodate:

- persons and person-types
- groups and collective forms
- investment domains
- constraints and prerequisites
- priorities and sequencing rules

These additions allow the repository to move from broad theory toward executable portfolios of action without collapsing personal, collective, and geopolitical analysis into one undifferentiated layer.
