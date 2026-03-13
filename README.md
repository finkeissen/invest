# Invest-GT

**Invest-GT** is a framework for understanding investment beyond money.

It studies how people, groups, institutions, and states invest **time, energy, money, attention, trust, health, education, coordination effort, and other scarce resources** in order to improve future outcomes under uncertainty.

The goal is not only to describe investment in theory, but to make it **practically usable**: for clearer priorities, better trade-offs, stronger life portfolios, and more coherent collective strategies.

> **Make inputs explicit. State hypotheses clearly. Model components separately. Validate them independently. Integrate them through declared interfaces.**

## What investment means here

In this repository, **investment** is used in a broad functional sense:

> the deliberate allocation of scarce resources in expectation of future gain under uncertainty

That gain is not limited to financial return.

Possible forms of gain include:

- financial gain
- health and vitality
- education and skill
- resilience and stability
- trust and social capital
- institutional capacity
- coordination ability
- strategic optionality
- long-term life improvement

This means that **a healthy life, education, relationships, stability, and orientation can all be treated as investments** if they improve future conditions for action and life.

Not all gains are directly comparable. Some trade-offs must remain visible instead of being hidden behind one single score.

## Core idea

The central claim of the repository is simple:

**Investment is broader than finance.**

A person invests when they use time, energy, money, or other resources to improve future life conditions.  
A household invests when it builds health, resilience, education, or stability.  
A group invests when it builds trust, coordination, shared knowledge, or durable structures.  
Institutions, firms, and states invest when they commit capital, legitimacy, policy capacity, or strategic effort toward future advantage.

The repository therefore treats investment as a general framework for thinking about:

- life goals
- priorities
- risks
- sequencing
- trade-offs
- maintenance burdens
- tailwinds and headwinds
- individual and collective gains
- collateral damage and distribution effects

## Personal and collective investment

A core distinction in this project is the difference between:

1. **investment from the perspective of the individual**
2. **investment from the perspective of the group**

These two levels are connected, but they are not identical.

A strategy may look beneficial at the group level while imposing severe losses on some individuals. In such cases, “group gain” must be examined carefully. Otherwise, a supposed collective success may hide redistribution, damage displacement, or a zero-sum structure.

For that reason, the framework asks at least two questions:

- What are the gains and losses for the individual person?
- What are the gains and losses across the group, including distribution and collateral damage?

This makes **positive-sum, zero-sum, destructive, and asymmetric outcomes** an essential part of evaluation.

## What the project is

Invest-GT is a framework for:

- broad investment thinking across multiple forms of capital
- life-portfolio design for individuals and groups
- practical priority-setting under constraints
- political-risk and geopolitical scenario analysis
- strategic interaction modeling across persons, groups, institutions, states, and markets
- hypothesis-driven simulation design
- local, reproducible experimentation
- disciplined translation from theory to implementation

## What the project is not

Invest-GT is **not**:

- a trading bot
- a portfolio-advice engine
- a prediction oracle
- direct financial advice
- a substitute for empirical validation
- a finished policy model
- a complete theory of human life or society

## What this framework should eventually enable

A mature version of the repository should help answer questions such as:

- What should a person prioritize first: safety, health, education, income, coordination, or recovery?
- Which investments increase future optionality?
- Which investments mainly preserve rather than expand?
- Which actions create hidden collateral damage?
- Which group strategies are positive-sum, and which are redistributive or destructive?
- How can life goals be translated into a realistic, executable plan?
- How can a person or group build a portfolio of actions rather than relying on isolated decisions?

The long-term ambition is to support the compilation of a **life plan** or **action portfolio** from a limited number of explicit inputs such as:

- goals
- constraints
- risks
- available resources
- time horizons
- dependencies
- expected benefits and harms for self and others

## Design principles

The repository follows a few non-negotiable principles:

1. **Explicit scope beats hidden assumptions.**
2. **Separate layers before integrating them.**
3. **A clear hypothesis is better than vague intuition.**
4. **Narratives are not evidence by themselves.**
5. **Validation must be possible in principle.**
6. **Practical usefulness matters.**
7. **Group gain must be checked for distribution and collateral damage.**
8. **Trade-offs should stay visible.**
9. **Maintenance and preservation are valid investments.**
10. **The avoidance of major downside can be more important than nominal upside.**

## Project posture

The project sits between several traditions:

- analytical philosophy
- functional philosophy
- systems thinking
- political economy
- scenario analysis
- strategic studies
- practical life design

The ambition is not only to describe systems, but to make them **actionable**.

A theory of investment is only useful if it can eventually support real-world decision portfolios for individuals and groups. That includes life goals, constraints, sequencing, maintenance burdens, tailwinds, headwinds, risk analysis, game-theoretic interaction, and review logic.

## Current themes in the repository

The repository currently gives special attention to:

- investment beyond finance
- personal and collective investment
- life goals as investment targets
- tailwinds and headwinds
- maintenance and preservation
- collateral damage and externalities
- lesser-evil trade-offs
- positive-sum vs. zero-sum outcomes
- risk, reversibility, and downside analysis
- the eventual compilation of life plans into executable portfolios

## Related approaches

Invest-GT is related to broader capital frameworks, life-design approaches, and systems-oriented impact frameworks, but combines them differently.  
See [docs/ecosystem-position.md](./docs/ecosystem-position.md) and [docs/related-approaches.md](./docs/related-approaches.md).

## Repository map

- [Pipeline Guide](./PIPELINE.md)
- [Docs](./docs/)
- [Decisions](./decisions/)
- [Pipeline](./pipeline/)

Major root folders may include:

- `agents/`
- `configs/`
- `data/`
- `docs/`
- `models/`
- `pipeline/`
- `reports/`
- `runtime/`
- `simulations/`
- `tests/`

## How to read the repository

### If you want the core idea first
Start with:

- `docs/overview.md`
- `docs/personal-and-collective-investment.md`
- `docs/life-portfolio-theory.md`
- this `README.md`

### If you want the practical direction
Then read:

- `docs/life-plan-compiler.md`
- `docs/collateral-damage-and-externalities.md`
- `pipeline/03_models/`
- `pipeline/00_inputs/priorities/`

### If you want the full bottom-up structure
Start with:

1. `pipeline/00_inputs/`
2. `pipeline/01_hypotheses/`
3. `pipeline/02_agents/`
4. `pipeline/03_models/`
5. `pipeline/04_runtime/`
6. `pipeline/05_simulations/`
7. `pipeline/06_tests/`
8. `pipeline/07_reports/`

Then move upward into:

- `docs/`
- `decisions/`
- `PIPELINE.md`
- this root `README.md`

## Status

The repository is an evolving framework.

Some parts are already structurally clear, especially the distinction between personal and collective investment, life-portfolio thinking, and the need to keep trade-offs, externalities, and risks visible. Other parts are still scaffolding and moving toward more operational form.

The current direction is to make the framework increasingly usable for:

- explicit decision support
- portfolio construction across life domains
- person/group priority analysis
- risk-aware action sequencing
- clearer translation from theory into execution

## For whom this repository may be useful

This repository may be relevant for people interested in:

- broad investment theory beyond finance
- practical philosophy
- life design under real constraints
- strategic thinking
- systems modeling
- individual and collective decision-making
- risk and trade-off analysis
- building coherent portfolios of action

## Standard of quality

At every stage, the repository should prefer:

- clear definitions over slogans
- modular structure over conceptual mixing
- explicit trade-offs over moral fog
- testable claims over rhetorical force
- practical next steps over abstract completionism
