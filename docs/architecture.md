# Architecture

## Modeling layers

### 1. Political / geopolitical layer
Models state action, policy shifts, conflict dynamics, alliances, sanctions, regulation, and strategic signaling.

### 2. Investment layer
Models how relevant actors allocate scarce resources under uncertainty. Depending on the use case, actors may include firms, funds, ministries, regulators, or other strategic institutions.

### 3. Game-theoretic layer
Provides the formal interaction structure: repeated games, Bayesian games, stochastic games, bargaining setups, and scenario-dependent payoff systems.

### 4. Propagation / feedback layer
Tracks how shocks and decisions propagate across incentives, constraints, expectations, and downstream outcomes.

### 5. Validation layer
Supports calibration, benchmarking, and comparison against historical episodes or structured external indicators.

## Methodology

The intended workflow is:

1. define structured inputs and scope boundaries
2. formulate hypotheses
3. model components in isolation
4. specify interfaces between components
5. integrate into a runtime
6. simulate and observe outputs
7. validate and revise

## Suggested repository structure

```text
agents/
configs/
data/raw/
data/processed/
docs/
hypotheses/
models/
notebooks/
pipeline/
prompts/
reports/
runtime/
scenarios/
simulations/
tests/
README.md
PIPELINE.md
```

## Operational note

The repository is intentionally split between **concept docs** and **pipeline work**. The conceptual explanation lives in `docs/`. The staged execution logic lives in `pipeline/`. This keeps the project readable even while it is still being designed.
