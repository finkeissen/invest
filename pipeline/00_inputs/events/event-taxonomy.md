# Event Taxonomy

## Purpose

This file defines the first event classes that Invest should recognize when turning real-world developments into structured inputs.

The taxonomy spans person-level, group-level, and geopolitical change.

## Level 1: Personal events

### Health and vitality events
- illness
- injury
- recovery
- burnout
- mental-health deterioration
- major improvement in fitness or recovery

### Education and capability events
- school or training started
- school or training completed
- certification gained
- skill decay
- major mentoring relationship formed

### Work and financial events
- job gained
- job lost
- promotion
- business launched
- debt shock
- emergency expense
- savings threshold reached

### Family and life-direction events
- marriage
- birth
- separation
- relocation
- caregiving burden increase
- conversion or major spiritual reorientation
- loss of meaning or direction

## Level 2: Group and institutional events

### Group cohesion events
- trust breakdown
- leadership transition
- split or schism
- successful coordination episode
- volunteer collapse
- reputational scandal

### Institutional events
- reform introduced
- funding loss or gain
- staffing crisis
- mission drift
- governance failure
- successful process upgrade

### Community and cultural events
- local security deterioration
- local recovery effort
- educational initiative launched
- religious renewal
- norm erosion
- norm repair

## Level 3: Geopolitical and market events

### Policy events
- sanctions announced
- sanctions tightened or relaxed
- export controls introduced
- tariffs imposed or removed
- subsidy or industrial-policy package announced
- capital-control change

### Political events
- election
- coalition breakdown
- leadership transition
- emergency decree
- referendum with strategic relevance

### Security and conflict events
- military escalation
- ceasefire or de-escalation
- territorial incursion
- proxy attack
- cyber disruption with strategic impact

### Economic and market events
- sovereign downgrade
- liquidity stress event
- banking stress event
- major supply-chain disruption
- commodity shock

### Coordination events
- alliance statement
- treaty breach
- joint industrial initiative
- failed negotiation
- coordinated intervention

## Normalized event fields

A structured event record should eventually contain at least:
- event id
- date or effective window
- level of analysis
- jurisdiction or affected region
- event class
- severity
- confidence or verification status
- expected channels of impact
- expected time horizon
- possible collateral damage

## Modeling note

Events should not be defined only by headlines.

An event matters when it changes expected options, constraints, incentives, damage, or timing for persons, groups, or systems.
