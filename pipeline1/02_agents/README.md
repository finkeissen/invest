# 02 Agents

This stage defines the decision-making actors used by the `invest` system.

An **agent** is any entity that can allocate resources, respond to conditions, and pursue goals under constraints. The purpose of this stage is to make actor behavior explicit enough for comparison, simulation, and revision.

This stage sits between:
- `00_inputs/`, which defines the world, domains, assets, events, indicators, and assumptions
- `01_hypotheses/`, which defines causal claims worth testing
- `03_models/`, which defines shared mechanisms and formal representations

## What belongs here

Use this folder for agent-specific definitions such as:
- actor profiles
- goals and priorities
- incentives
- constraints
- capabilities
- information and belief structures
- decision rules
- adaptation logic
- coordination styles
- failure modes

Rule of thumb:
- Put **actor-specific behavior** here
- Put **shared mechanism logic** in `03_models/`
- Put **empirical claims** in `01_hypotheses/`

## Why agents matter

The same event does not affect every actor in the same way.
A tariff shock, illness, liquidity stress, or trust breakdown may lead to different decisions depending on:
- available capital
- time horizon
- institutional role
- risk tolerance
- cultural commitments
- moral limits
- access to support and coordination

Without explicit agents, the project collapses into abstract claims without actionable pathways.

## Agent levels in `invest`

`invest` should support more than one layer of agency.

### 1. Personal agents
Examples:
- individual person
- household
- family

Typical concerns:
- health
- learning
- work and income
- habits
- relationships
- meaning and direction
- resilience

### 2. Group agents
Examples:
- team
- local community
- school or learning group
- firm
- institution
- religious community

Typical concerns:
- trust
- coordination
- role stability
- shared knowledge
- conflict management
- continuity
- mission

### 3. Macro agents
Examples:
- state
- regulator
- central bank
- alliance
- geopolitical bloc
- strategic firm

Typical concerns:
- policy
- capital allocation
- industrial capacity
- deterrence
- legitimacy
- systemic resilience

Not every project run must use all levels. However, the repository should keep the taxonomy open enough to support them.

## Minimum agent schema

Each agent definition should answer these questions.

### Identity
- What kind of agent is this?
- At what level does it operate: person, group, or macro actor?
- What boundaries define it?

### Objectives
- What does the agent seek to protect?
- What does the agent seek to grow?
- What trade-offs is it willing to make?

### Capital base
What forms of capital does the agent hold or depend on?
For example:
- financial capital
- health capital
- knowledge capital
- time capacity
- relationship capital
- institutional capital
- trust capital

### Constraints
- hard constraints
- soft constraints
- legal constraints
- moral constraints
- biological constraints
- coordination constraints

### Information and beliefs
- What can the agent observe?
- What does it infer?
- What does it likely misunderstand?
- How quickly can it update?

### Decision rules
- How does the agent choose among options?
- Does it optimize, satisficice, imitate, preserve buffers, or follow doctrine?
- What triggers action, delay, escalation, retreat, or review?

### Adaptation
- Can the agent learn?
- Can it reallocate?
- Can it coordinate with others?
- Can it survive a mistaken choice?

### Failure modes
- overreach
- paralysis
- short-termism
- narrative capture
- moral injury
- coordination breakdown
- self-undermining success

## Agent design principles

### Keep behavior legible
Agent descriptions should be simple enough to inspect and debate.
Avoid fake precision.

### Separate goals from methods
A group may value trust but use poor methods to preserve it.
Do not conflate declared goals with actual decision rules.

### Preserve asymmetry
A household and a state are not scaled versions of each other.
Do not flatten different forms of agency into one template.

### Include non-financial agency
Some high-impact actors in life investment are not market actors.
Examples include caregivers, teachers, households, local organizers, and religious communities.

### Model limits explicitly
Agents do not act with perfect foresight.
Bounded rationality is a feature, not a bug.

## Recommended file pattern

If this stage grows, one useful structure is:

- `agent-template.md`
- `person-agent.md`
- `household-agent.md`
- `community-agent.md`
- `firm-agent.md`
- `state-agent.md`

These files do not all need to exist immediately. The stage can start with a README and expand when concrete simulation or planning work requires it.

## Outputs of this stage

A completed agent layer should make it possible to answer:
- who decides
- with what goals
- under what limits
- using which rules
- with what likely blind spots
- and with what adaptation capacity

That output is then usable by runtime logic, scenario design, and evaluation.

## Common mistakes

Avoid:
- treating all actors as utility maximizers
- assuming access to identical information
- ignoring non-financial forms of capital
- confusing institutional role with moral legitimacy
- describing agents so vaguely that no prediction follows
- describing agents so rigidly that no adaptation is possible

## Relation to the larger repository

This stage is one bridge from theory to action.

If `invest` aims to support real people and real groups in building practical investment portfolios, then agents cannot be limited to states, regulators, and funds. The repository must also support persons, households, communities, and other durable units of life organization.

That does not weaken the geopolitical use case. It makes the framework more general, more honest, and more usable.
