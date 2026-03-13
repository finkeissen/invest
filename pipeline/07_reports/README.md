# 07 Reports

This stage converts simulation output into usable findings.

Its job is not only to show what happened in a run, but to make the result interpretable, reviewable, and actionable. A report should help a reader understand:

- what was tested
- what the system produced
- why the result matters
- how confident the team should be
- what remains uncertain
- what the next decision should be

## Purpose

Reports sit between technical execution and practical use.

They turn raw outputs into structured findings that can be used by researchers, operators, contributors, and decision-makers. A good report is concise enough to read quickly, but explicit enough that another person can trace the logic from inputs to conclusions.

## Core reporting principles

Every report should distinguish clearly between the following layers:

1. **Result**  
   What the simulation or run produced.

2. **Explanation**  
   Why the result likely occurred, based on the model, assumptions, and runtime conditions.

3. **Confidence**  
   How stable, sensitive, or fragile the finding appears to be.

4. **Limitations**  
   What the report cannot establish, what was excluded, and where interpretation may fail.

5. **Decision relevance**  
   What the result suggests for further testing, strategy, prioritization, or documentation.

## Typical contents

A report at this stage may contain:

- run summaries
- interpretation notes
- assumptions behind results
- sensitivity observations
- failure cases
- next-step recommendations
- comparison across scenarios
- confidence notes and caveats

## Minimum report structure

A standard report should include the following sections:

### 1. Scope

- run or simulation identifier
- hypothesis or scenario tested
- date or snapshot reference
- relevant agent and model references

### 2. Inputs and setup

- key assumptions used
- major parameters
- important exclusions
- runtime or configuration notes

### 3. Main result

- central output or outcome
- whether the result confirms, weakens, or contradicts the working hypothesis

### 4. Interpretation

- likely causal drivers
- interactions worth noting
- meaningful secondary effects

### 5. Sensitivity and robustness

- whether the result changes materially under different assumptions
- which variables matter most
- where confidence breaks down

### 6. Limitations

- missing inputs
- structural blind spots
- unresolved ambiguity
- possible overfitting to a narrow scenario

### 7. Recommended next steps

- further simulation
- model revision
- better data collection
- documentation update
- no action

## Style guidance

Reports should be:

- explicit rather than impressionistic
- concise rather than bloated
- test-linked rather than purely narrative
- decision-relevant rather than ornamental

Avoid presenting narrative confidence as evidence. If a claim depends on an assumption, say so directly.

## Relationship to the wider repository

This stage is closely related to:

- `reports/` for persistent report outputs
- `notebooks/` for exploratory interpretation
- `docs/` for longer-form conceptual writeups
- `pipeline/06_tests/` for validation context
- `pipeline/05_simulations/` for the run context that generated the report

## Future extension

If the repository continues to expand from geopolitical analysis toward broader personal and collective investment logic, reports may later include additional sections for:

- person-level outcomes
- group-level gains and losses
- collateral damage and externalities
- trade-off framing across multiple kinds of value
- life-planning relevance and priority implications

This stage should remain neutral and disciplined: it reports findings clearly before turning them into doctrine.
