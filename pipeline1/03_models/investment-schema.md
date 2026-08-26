# Investment Schema

## Purpose

This file defines a standard object schema for representing any investment in Invest-GT.

The schema is broad enough to represent:
- personal investments,
- household investments,
- group investments,
- institutional investments,
- geopolitical or market investments.

A shared schema keeps evaluation legible across very different domains.

---

## Core principle

An investment record should not only say what is pursued. It should also say:
- for whom,
- at what cost,
- under which risks,
- with which prerequisites,
- with which externalities,
- on what timeline,
- with what review logic.

---

## Minimal fields

### Identity
- investment id
- investment name
- level of analysis
- owner or deciding actor
- affected actors

### Intent
- target domain
- stated objective
- expected gain dimensions
- time horizon
- rationale

### Resource commitment
- money required
- time required
- attention required
- energy burden
- coordination burden
- maintenance burden

### Dependency structure
- prerequisites
- enabling conditions
- dependencies on other investments
- sequencing position

### Risk structure
- key risks
- downside severity
- reversibility
- uncertainty class
- failure triggers

### Effects
- benefits to self
- harms to self
- benefits to others
- harms to others
- distribution pattern
- externalities
- collateral damage risk

### Strategic classification
- compounding or non-compounding
- maintenance or growth
- optionality-building or lock-in
- positive-sum, zero-sum, or destructive tendency

### Execution
- start condition
- cadence
- stop rule
- review date
- evidence or indicator set

---

## Minimal template

```text
Investment ID:
Investment Name:
Level:
Deciding Actor:
Affected Actors:

Objective:
Target Domain:
Expected Gain Dimensions:
Time Horizon:
Rationale:

Money Required:
Time Required:
Attention Required:
Energy Burden:
Coordination Burden:
Maintenance Burden:

Prerequisites:
Enabling Conditions:
Dependencies:
Sequencing Position:

Key Risks:
Downside Severity:
Reversibility:
Uncertainty Class:
Failure Triggers:

Benefits to Self:
Harms to Self:
Benefits to Others:
Harms to Others:
Distribution Pattern:
Externalities:
Collateral Damage Risk:

Compounding Status:
Maintenance vs Growth:
Optionality Effect:
Strategic Classification:

Start Condition:
Cadence:
Stop Rule:
Review Date:
Indicators:
```

---

## Modeling rule

No major investment should be represented only by expected upside.

At minimum, its prerequisite structure, downside, reversibility, and effects on others must remain visible.
