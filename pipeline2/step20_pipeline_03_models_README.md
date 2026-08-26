# 03 Models

This stage defines the shared formal structures that transform hypotheses, inputs, and agent behavior into analyzable outcomes.

Models are not narratives and not biographies. They are explicit representations of how states change, how incentives interact, how constraints bind, and how consequences propagate across time.

In the original geopolitical and market-focused repository, this layer mainly captures cross-actor strategic logic. In the broader invest framework, it also supports person-level, household-level, group-level, institutional, and geopolitical models.

It also now has to support a more explicit protective layer: not only how resources generate gain, but how allocations defend critical conditions of life, buffer shocks, preserve recoverability, and prevent movement into irreversible or near-irreversible states.

## Purpose

The purpose of `03_models` is to define reusable formal structures that can later be executed, stress-tested, compared, or rejected.

A model in this stage should answer questions like:

- What are the relevant state variables?
- What changes those variables?
- Which actors or levels interact?
- Which constraints are hard and which are soft?
- How does one action produce first-order and second-order effects?
- Which trade-offs are assumed?
- What counts as gain, loss, resilience, or failure?
- Which conditions must be protected before expansion is even meaningful?
- Where are the critical thresholds, protection gaps, and recoverability limits?

This stage is the bridge between conceptual claims and operational runtime logic.

## What belongs here

Examples of appropriate model content include:

- payoff structures
- transition rules
- state update logic
- trade-off models
- propagation mechanisms
- coordination and conflict models
- policy or market response functions
- portfolio allocation logic
- personal and household priority models
- risk models
- optionality and reversibility models
- collateral damage and externality models
- threshold-defense models
- shock-buffering and recoverability models
- protection-coverage and false-safety models

## What does not belong here

The following should remain elsewhere:

- raw observations and source material -> `00_inputs`
- tentative causal claims -> `01_hypotheses`
- actor descriptions and incentives -> `02_agents`
- executable orchestration and run control -> `04_runtime`
- concrete scenario runs -> `05_simulations`
- evaluation and falsification procedures -> `06_tests`
- human-facing summaries -> `07_reports`

Rule of thumb:

> Put cross-state logic here, not unstructured explanation.

## Design principles

### 1. Models must make structure explicit

A model should clearly declare:

- levels of analysis
- key variables
- state transitions
- objectives or utility assumptions
- constraints
- known blind spots
- defended thresholds
- recoverability assumptions

### 2. Models must stay separable from hypotheses

A hypothesis says that some effect may occur.
A model specifies one explicit structure through which such an effect would occur.

Multiple models may represent the same hypothesis.
One model may support several related hypotheses.

### 3. Models must support multiple levels

The broader invest framework needs at least these model families:

- person-level models
- household-level models
- group-level models
- institutional models
- geopolitical models

A good model states which level it operates on and which adjacent levels it depends on.

### 4. Models must preserve non-financial dimensions

Not every gain is monetary. Models may need to represent:

- health
- knowledge
- energy
- trust
- time
- security
- optionality
- meaning or normative coherence

Where dimensions are not safely reducible to one scalar score, the model should keep them separate.

### 5. Models must expose collateral damage

A model should not only represent intended gains. It should also identify:

- spillovers
- burdens shifted to others
- hidden maintenance costs
- delayed losses
- irreversible harms
- fragility shifted across actors or time

### 6. Models should prefer governed simplicity

A simple model that declares its limits is often better than a large pseudo-precise model.

### 7. Models must distinguish expansion from protection

Not every allocation problem is mainly about growth or gain. Some are primarily about:

- preserving minimum viable conditions
- buffering shock exposure
- transferring risks
- supporting recovery after loss
- keeping room for adaptation under stress

A model should make that orientation explicit.

### 8. Models must represent false safety where relevant

Formal coverage is not identical to practical resilience.

A model should distinguish between:

- nominal protection and real protection
- local stability and system-wide fragility
- first-order protection success and second-order protection failure
- apparent coverage and actual recoverability

## Suggested model families

### A. Outcome models

These define what counts as success, failure, and acceptable trade-off.

Examples:

- expected gain under uncertainty
- downside-limited gain
- resilience-first objective
- sufficiency before optimization
- threshold-preservation before expansion

### B. Transition models

These define how states move from one condition to another.

Examples:

- health depletion and recovery
- education compounding
- capital flight under political stress
- trust erosion after coordination failure
- shock absorption and post-loss recovery

### C. Interaction models

These define how actors influence one another.

Examples:

- policy-response interaction
- alliance coordination
- household role balancing
- employer-worker incentive structure
- leader-group trust loop
- protection burden shifting across actors

### D. Allocation models

These define how scarce resources are distributed.

Examples:

- time allocation
- capital allocation
- attention allocation
- institutional budget allocation
- effort allocation across competing life goals
- protection versus expansion allocation

### E. Constraint models

These define what cannot simply be optimized away.

Examples:

- biological limits
- debt burden
- legal restrictions
- moral prohibitions
- security constraints
- minimum viability thresholds
- recoverability limits

### F. Externality models

These define who else is affected and how.

Examples:

- one group gains while another absorbs risk
- industrial policy reallocates resilience and cost
- personal overwork raises short-run output but destroys long-run health
- one actor's protection strategy displaces fragility onto others

## Minimal model schema

Each model document should ideally include:

1. Model name
2. Model ID
3. Scope and level
4. Objective
5. Variables
6. Assumptions
7. Transition logic
8. Constraints
9. Gain and loss definitions
10. Externalities
11. Failure modes
12. Inputs required
13. Outputs produced
14. Validation notes
15. Known exclusions
16. Protected conditions
17. Critical thresholds
18. Recoverability notes
19. False-safety checks

## Recommended future files in this folder

As the repository expands, this folder may include files such as:

- `model-template.md`
- `model-family-personal-capital.md`
- `model-family-group-coordination.md`
- `model-family-geopolitical-repricing.md`
- `model-family-risk-and-optionality.md`
- `model-family-collateral-damage.md`
- `model-family-threshold-defense.md`
- `model-family-recoverability.md`
