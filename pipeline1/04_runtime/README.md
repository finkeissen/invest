# 04 Runtime

This stage turns the analytical pipeline into an executable run.

The runtime layer is responsible for taking the outputs of prior stages and compiling them into a reproducible execution context. It defines how inputs, hypotheses, agents, and models are assembled; how run configuration is resolved; how randomness is seeded; how logs are written; and how outputs are tagged for later comparison.

In the broader `invest` framework, runtime is where theory becomes operational. A sound runtime does not decide what is true by itself. Instead, it ensures that a chosen set of assumptions can be executed consistently, inspected afterwards, and rerun under the same conditions.

## Purpose

The purpose of `04_runtime` is to define the rules for:

- building a run from selected inputs,
- resolving configuration and execution order,
- controlling determinism and randomness,
- capturing metadata and logs,
- and making runs reproducible across time and environments.

This stage should make it possible to answer questions such as:

- What exactly was executed?
- In what order were components assembled?
- Which assumptions and parameters were active?
- Which seed values and runtime settings were used?
- Can the same run be reproduced later?

## Scope

This folder should define runtime conventions, not full business logic.

In scope:

- execution orchestration,
- run manifests,
- configuration resolution,
- seed and randomness conventions,
- logging and trace conventions,
- output naming and run IDs,
- environment assumptions,
- reproducibility rules.

Out of scope:

- the substantive content of inputs,
- hypothesis authoring,
- agent definitions,
- model design,
- simulation result interpretation,
- final report writing.

## Runtime Principles

### 1. Reproducibility before convenience
A run should be easy to reproduce even if that requires more metadata, stricter naming, or explicit configuration.

### 2. Explicit over implicit
Every meaningful runtime choice should be visible in configuration, manifests, or logs.

### 3. Stage discipline
The runtime may assemble outputs from prior stages, but it should not silently redefine them.

### 4. Determinism where possible
If a run depends on randomness, the source of randomness should be documented and controllable.

### 5. Traceability
Every run should leave a trace that can be inspected later by a human reviewer.

### 6. Separation of execution and interpretation
The runtime executes. Reports interpret.

## Core Runtime Responsibilities

### Run assembly
The runtime should define how to:

- select the relevant snapshot or input set,
- load hypotheses,
- instantiate agents,
- bind models,
- and prepare the execution context.

### Execution order
The runtime should define the order in which components are evaluated. This includes:

- initialization,
- pre-run validation,
- simulation or execution steps,
- checkpointing,
- and post-run output collection.

### Configuration resolution
A run may depend on defaults, environment-specific settings, scenario-specific overrides, and explicit user parameters. The runtime should define a consistent precedence order.

Example precedence:

1. hard-coded engine constraints,
2. base defaults,
3. scenario configuration,
4. explicit run-level overrides.

### Seed handling
If stochastic components are present, the runtime should define:

- where the seed is set,
- whether one seed or multiple derived seeds are used,
- how seed values are recorded,
- and which components are allowed to depend on seeded randomness.

### Logging and traces
Each run should emit enough information to reconstruct what happened. A minimal trace usually includes:

- run ID,
- timestamp,
- selected scenario,
- input snapshot reference,
- active hypotheses,
- active agents,
- active models,
- seed values,
- validation results,
- output locations,
- warnings and failures.

### Output packaging
The runtime should define conventions for writing outputs so that runs are comparable over time.

Examples:

- one folder per run,
- machine-readable manifest,
- human-readable summary,
- checksums or version hashes,
- stable naming conventions.

## Recommended Artifacts

Typical artifacts generated or referenced by the runtime include:

- `run-manifest.json` or `.yaml`
- `run-log.txt` or structured logs
- `config-resolved.yaml`
- `seed-record.json`
- `component-registry.json`
- `output-index.json`

These do not all need to live in this folder, but this folder should define the convention for them.

## Relation to the Broader Invest Framework

In a narrow geopolitical-market version of the project, runtime executes scenario runs and model combinations.

In a broader personal-and-collective investment framework, runtime also matters for:

- life-plan compilation,
- portfolio comparisons across domains,
- person versus group evaluation modes,
- priority ladder selection,
- and explicit collateral-damage accounting.

That does not mean runtime should contain ethical theory. It means runtime must be able to carry the chosen ethical and evaluative settings into execution without ambiguity.

## Folder Expectations

This folder may eventually contain documents such as:

- runtime architecture notes,
- configuration precedence rules,
- run manifest specification,
- seeding policy,
- logging conventions,
- reproducibility checklist.

## Minimal Standard for This Stage

A minimally acceptable runtime layer should guarantee that:

- the executed configuration can be reconstructed,
- seeded behavior is repeatable,
- component selection is visible,
- outputs are tied to a specific run,
- and execution failures can be diagnosed.

## Interfaces to Neighboring Stages

### Inputs from previous stages
- `00_inputs`: scoped assumptions and snapshots
- `01_hypotheses`: candidate causal statements
- `02_agents`: executable actor definitions
- `03_models`: model structures and mappings

### Outputs to later stages
- `05_simulations`: executable simulation runs
- `06_tests`: runtime validation and invariants
- `07_reports`: structured summaries and interpretations

## Related Repository Folders

Likely related implementation folders elsewhere in the repository:

- `runtime/`
- `configs/`
- `simulations/`
- `tests/`
- `reports/`

## Design Standard

The runtime should be boring in the best sense: clear, explicit, auditable, and dependable. If the runtime is confusing, the results above it become difficult to trust.
