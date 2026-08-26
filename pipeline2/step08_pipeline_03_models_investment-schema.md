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


In the current extension of the framework, the schema must also be able to represent investments whose primary function is not expansion but protection, buffering, threshold defense, recoverability, or adaptation under stress.

---

## Core principle

An investment record should not only say what is pursued. It should also say:
- for whom,
- what it protects,
- which thresholds it defends,
- what kind of failure it is meant to prevent or soften,
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
- protective function
- protected conditions
- defended thresholds
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
- irreversibility risk
- uncertainty class
- failure triggers
- shock profile
- coverage gaps

### Effects
- benefits to self
- harms to self
- benefits to others
- harms to others
- distribution pattern
- externalities
- collateral damage risk
- recoverability effect
- buffering effect
- fragility transfer risk

### Strategic classification
- compounding or non-compounding
- maintenance or growth
- protection or expansion
- optionality-building or lock-in
- positive-sum, zero-sum, or destructive tendency
- prevention, mitigation, buffering, transfer, recovery, or adaptation mode

### Execution
- start condition
- cadence
- stop rule
- review date
- evidence or indicator set
- protection review logic
- false-safety checks

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
Protective Function:
Protected Conditions:
Defended Thresholds:
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
Irreversibility Risk:
Uncertainty Class:
Failure Triggers:
Shock Profile:
Coverage Gaps:

Benefits to Self:
Harms to Self:
Benefits to Others:
Harms to Others:
Distribution Pattern:
Externalities:
Collateral Damage Risk:
Recoverability Effect:
Buffering Effect:
Fragility Transfer Risk:

Compounding Status:
Maintenance vs Growth:
Protection vs Expansion:
Optionality Effect:
Strategic Classification:
Protection Mode:

Start Condition:
Cadence:
Stop Rule:
Review Date:
Indicators:
Protection Review Logic:
False-Safety Checks:
```

---

## Modeling rule

No major investment should be represented only by expected upside.

At minimum, its prerequisite structure, downside, reversibility, and effects on others must remain visible.


---

## Additional modeling note for protective investments

Some investments primarily aim at gain; others primarily aim at preserving viability under stress. The schema should make that difference explicit.

A protective investment is underdescribed if it only states cost and nominal coverage. It should also show:
- which threshold it is defending,
- which failure mode it assumes,
- what remains uncovered,
- how recovery would actually work after shock,
- and how the protection itself could create maintenance burdens, complacency, or shifted harms.
