# Pipeline

Invest-GT is easiest to operationalize as a staged research pipeline rather than as a monolithic model. The goal is to move from explicit assumptions to reproducible runs and structured evaluation.

## Recommended pipeline

### 00. Inputs and world modeling
Define the baseline world representation used by all downstream work:
- actors, institutions, alliances, blocs
- macro variables and policy variables
- event types and constraints
- asset universe or allocation targets
- scenario assumptions and time horizon

Primary workspace:
- `pipeline/00_inputs/`

### 01. Hypothesis definition
Write down the claims the system is supposed to test before building runtime logic.

Primary workspace:
- `pipeline/01_hypotheses/`
- `hypotheses/`

### 02. Agent design
Specify actors, incentives, constraints, beliefs, and strategy spaces.

Primary workspace:
- `pipeline/02_agents/`
- `agents/`

### 03. Model design
Define payoff structures, update rules, interaction forms, and propagation logic.

Primary workspace:
- `pipeline/03_models/`
- `models/`

### 04. Runtime assembly
Connect the separate components through explicit interfaces and configuration rules.

Primary workspace:
- `pipeline/04_runtime/`
- `runtime/`
- `configs/`

### 05. Simulations
Execute scenarios, sweeps, and experiment variants.

Primary workspace:
- `pipeline/05_simulations/`
- `simulations/`

### 06. Tests and validation
Compare outputs against consistency checks, benchmarks, and historical anchors.

Primary workspace:
- `pipeline/06_tests/`
- `tests/`
- `notebooks/`

### 07. Reports
Translate outputs into usable research findings and limitations.

Primary workspace:
- `pipeline/07_reports/`
- `reports/`
- `docs/`

## Practical flow

1. define or update the world state in `pipeline/00_inputs/`
2. define a scenario or research question
3. write a hypothesis in `pipeline/01_hypotheses/`
4. specify actors and decision logic
5. formalize the interaction model
6. assemble and run the runtime
7. test and interpret the results
8. summarize the run and its limitations

## Why this structure fits Invest-GT

This project sits at the intersection of politics, strategic interaction, and investment behavior. That work becomes hard to reason about when assumptions, scenarios, model logic, and outcomes are mixed together. A pipeline-first structure keeps those concerns legible and versionable.
