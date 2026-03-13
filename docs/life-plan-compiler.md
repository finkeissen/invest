# Life Plan Compiler

## Purpose

This document defines how Invest-GT should eventually turn a small number of explicit human inputs into an executable life portfolio.

The idea is not to replace judgment. The idea is to make judgment more structured, more legible, and more practically usable.

A life-plan compiler should accept a limited set of declared goals, constraints, and conditions, and transform them into:
- a sequence of priorities,
- a manageable portfolio of actions,
- a timing structure,
- a reason record,
- explicit trade-offs for self and others.

---

## Core claim

With few but explicit inputs, a person should be able to generate a first practical life plan.

The output is not a final destiny. It is a structured starting portfolio that can be executed, reviewed, and revised.

The compiler should answer:
- what to do,
- when to do it,
- why it comes first,
- what it costs,
- what it enables later,
- what it risks for oneself,
- what it risks for others.

---

## Minimal input set

A first version of the compiler should work from a deliberately small input surface.

### 1. Life goals

The system should support a bounded set of selectable goals such as:
- survival and safety
- health and vitality
- stability and order
- education and competence
- income and financial resilience
- family and relationship quality
- freedom and optionality
- contribution and service
- meaning and spiritual coherence
- institutional or community building

The user does not need to select all of them.

### 2. Current condition

The compiler should record at least:
- health condition
- energy level
- cash buffer or financial stress
- schedule control
- dependents or care obligations
- social support quality
- current work condition
- current education or skill level
- major active headwinds

### 3. Constraints

The compiler should record:
- money constraints
- time constraints
- physical constraints
- legal constraints
- moral constraints
- geographic constraints
- family constraints
- institutional constraints

### 4. Risk tolerance and reversibility

The system should ask:
- how much downside can be tolerated,
- what losses would be catastrophic,
- which actions are reversible,
- which commitments should remain optional.

### 5. Affected others

The compiler should ask who else is materially affected by the plan:
- spouse or partner
- children
- parents or dependents
- team or group members
- local community
- institution or organization

---

## Compilation logic

The compiler should proceed in layers rather than trying to optimize everything at once.

### Layer 1: Prevent collapse

First address catastrophic downside and major headwinds.

Examples:
- untreated health breakdown
- severe sleep deprivation
- acute debt spiral
- unsafe housing
- addiction
- relationship chaos with strong downstream effects
- legal exposure

### Layer 2: Secure prerequisites

Second secure conditions without which higher goals cannot be executed well.

Examples:
- sleep and baseline health
- emergency savings buffer
- schedule control
- basic literacy or skill repair
- minimum social support
- baseline order and routine

### Layer 3: Build compounding capacities

Only then should the portfolio heavily emphasize high-upside compounding domains.

Examples:
- education
- skill accumulation
- financial accumulation
- habit systems
- relationship strengthening
- trust and reputation
- spiritual discipline where relevant

### Layer 4: Expand optionality

After prerequisites are reasonably stable, the system should prefer investments that broaden future choice.

Examples:
- language learning
- portable skills
- geographic flexibility
- savings and liquidity
- durable networks
- institutional credibility

### Layer 5: Pursue higher-order projects

Finally, the plan may allocate serious effort toward long-range projects such as:
- family formation
- institution building
- public contribution
- major creative work
- political or civic engagement
- mission-driven or religious commitments

---

## Output format

Each compiled plan should produce at least the following sections.

### 1. Ordered priorities

A ranked list of what comes first and why.

### 2. Action portfolio

A set of concrete actions with:
- action name
- target domain
- effort class
- start timing
- frequency or cadence
- expected gain
- expected downside
- prerequisites
- review date

### 3. Trade-off record

For each major action:
- benefits for self,
- costs for self,
- benefits for others,
- costs for others,
- whether the action is mostly positive-sum, redistributive, or destructive.

### 4. Dependency map

The plan should state which actions unlock others.

### 5. Stop and revise rules

The plan should state when to stop, pause, or revise because reality changed.

---

## Practical decision rules

A first practical compiler should follow rules like these:
- remove large avoidable headwinds before adding ambitious new projects,
- do not buy upside by destroying health,
- do not call a strategy a group success if it quietly sacrifices identifiable persons,
- preserve optionality under uncertainty,
- protect maintenance and preservation work from being invisibly crowded out,
- prefer positive-sum creation over zero-sum transfer when both are available,
- use lesser-evil logic only when cleaner options are truly unavailable.

---

## Self and others

The compiler must not evaluate a person only as an isolated unit.

A strong life plan should show both:
1. what the plan does for the actor,
2. what the plan does to surrounding persons and groups.

This matters because some plans improve one life by externalizing hidden damage onto others. The system should keep those costs explicit.

---

## Relation to the repository

This document should connect to:
- `docs/life-portfolio-theory.md`
- `docs/personal-and-collective-investment.md`
- `docs/collateral-damage-and-externalities.md`
- `pipeline/00_inputs/priorities/`
- `pipeline/03_models/investment-schema.md`
- `pipeline/03_models/model-family-life-portfolio.md`
- `pipeline/03_models/model-family-risk-and-reversibility.md`

---

## Maturity target

A mature Invest-GT implementation should eventually allow a person or group to declare a small set of goals and constraints and receive a draft portfolio that is:
- understandable,
- challengeable,
- revisable,
- ethically legible,
- practically executable.
