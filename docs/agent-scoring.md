# Agent Scoring

This document defines how Invest-GT should evaluate whether an agent performed well in a simulation round or scenario.

The central principle is simple: an agent should not be scored only on whether its output sounds plausible. It should be scored on whether its behavior is consistent with its role, information set, constraints, strategy, and realized outcomes.

## Why this document exists

`validation.md` defines the broader validation philosophy of the repository. This document handles a narrower and harder problem:

**How do we judge agent quality in a way that is reproducible, comparable, and not reducible to surface-level fluency?**

That matters especially when agent reasoning may be produced by LLMs. Fluent language can hide weak strategy, broken assumptions, or inconsistent actions.

## Scoring dimensions

Each agent action or action sequence should be scored across several dimensions.

### 1. Role consistency

Does the agent behave like the type of actor it is supposed to represent?

Examples:
- a regulator should not optimize exactly like a hedge fund,
- a sovereign actor should treat political stability differently from a short-horizon trader,
- a firm should care about margins, access, and continuity constraints.

### 2. Information consistency

Did the agent act on information it plausibly had at the time?

This guards against:
- hindsight leakage,
- impossible foresight,
- and decisions that rely on unavailable signals.

### 3. Constraint consistency

Did the agent respect budget, mandate, institutional, legal, or political constraints?

Examples:
- sanctions compliance,
- leverage limits,
- electoral constraints,
- procurement limits,
- capital controls.

### 4. Strategic coherence

Are the agent's action, explanation, and objective aligned?

This checks whether the stated rationale matches the actual move.

### 5. Outcome quality

Did the decision improve the agent's objective relative to baseline?

This should be evaluated relative to the role:
- return or risk-adjusted return for allocators,
- stability or deterrence objective for state actors,
- resilience or continuity for firms,
- compliance and control objectives for regulators.

### 6. Adaptation quality

Did the agent update sensibly when the environment changed?

This matters in multi-round simulations. Good play is not static play.

### 7. Externality awareness

Did the agent appropriately account for second-order effects where its role requires it?

Examples:
- a regulator should consider spillovers,
- a state actor should consider alliance reactions,
- a large allocator should consider liquidity and crowding effects.

## Suggested scoring rubric

A practical first rubric is a 0-4 score on each dimension:

- **0** = broken or absent
- **1** = weak
- **2** = partially adequate
- **3** = strong
- **4** = excellent

This yields a structured scorecard rather than a single opaque judgment.

## Weighting by actor class

Not every dimension should count equally for every actor.

### Example weighting logic

**State actor**
- role consistency: high
- information consistency: high
- constraint consistency: high
- strategic coherence: high
- outcome quality: medium-high
- adaptation quality: medium
- externality awareness: high

**Allocator / investor**
- role consistency: medium
- information consistency: high
- constraint consistency: high
- strategic coherence: high
- outcome quality: very high
- adaptation quality: high
- externality awareness: medium

**Firm / producer**
- role consistency: high
- information consistency: high
- constraint consistency: high
- strategic coherence: high
- outcome quality: high
- adaptation quality: medium-high
- externality awareness: medium

## Baselines for comparison

Agent performance should never be read in isolation. Compare against at least one baseline.

Recommended baselines:

1. **Rule-based baseline**
   A simple scripted policy or decision heuristic.

2. **No-adaptation baseline**
   The same role with static behavior across rounds.

3. **Randomized constrained baseline**
   Actions sampled within valid constraints, but without strategic reasoning.

4. **Ablation baseline**
   Remove one reasoning layer, such as narrative interpretation or second-order response modeling.

## Failure modes to track

The scoring system should explicitly record recurring failure patterns.

Examples:
- narrative fluency without strategic substance,
- internal contradiction between rationale and action,
- overreaction to noisy signals,
- underreaction to regime change,
- objective drift,
- role collapse across agents,
- hidden hindsight,
- unrealistic certainty.

## Minimal evaluation record

Each evaluated run should ideally record:

- scenario id,
- timestamp or round,
- actor id / class,
- objective,
- information available,
- action taken,
- explanation,
- realized outcome,
- baseline comparison,
- dimension scores,
- brief evaluator note.

## What counts as a good agent?

A good agent is not one that always "wins." A good agent is one that:

- behaves credibly for its role,
- uses only appropriate information,
- respects constraints,
- adapts coherently,
- and produces outcomes that are meaningfully better than baseline often enough to justify its complexity.

## Relation to validation

This document should be used together with `docs/validation.md`.

- `validation.md` asks whether the system is valid at the framework level.
- `agent-scoring.md` asks whether a given agent instance is valid at the behavioral level.

Both are required for serious evaluation.
