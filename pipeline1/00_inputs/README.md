# 00 Inputs

This stage defines the structured starting point for Invest.

The goal of `00_inputs/` is to make starting assumptions explicit before they enter hypotheses, agent logic, models, simulations, or reports. Nothing downstream should rely on hidden world-state choices.

## Purpose

`00_inputs/` collects the minimum documented representation of the world required to build practical investment reasoning for both individuals and groups.

This includes:
- coverage boundaries
- actor classes
- person and group classes
- asset and capital classes
- event taxonomies
- indicator families
- domain taxonomies
- constraints and prerequisites
- baseline assumptions
- reproducible snapshots
- human, group, and geopolitical domains

## Design principle

Invest is broader than finance.

In this repository, an investment is any deliberate use of scarce resources that aims to produce future gain under uncertainty. Financial allocation is one important case, but not the only one.

Investments may target:
- financial return
- health
- education
- capability
- social trust
- institutional strength
- security
- meaning and life direction

## Output of this stage

A clean, documented, reusable input state that can feed:
- hypotheses
- agent definitions
- model specifications
- scenario generation
- simulation execution
- life-planning and portfolio design

## Minimum standard

Before any input is used downstream, it should state:
- scope
- intended level of analysis
- provenance or source class
- update cadence
- known limitations
- intended downstream use

## Folder map

- `actors/` — who acts
- `persons/` — person-level starting conditions and person types
- `groups/` — collective forms and group-level constraints
- `domains/` — investment domains and capability areas
- `priorities/` — priority and sequencing heuristics
- `constraints/` — prerequisites, bottlenecks, and hard limits
- `assets/` — what can be accumulated, allocated, protected, or exchanged
- `assumptions/` — baseline methodological and practical assumptions
- `events/` — what changes the world state
- `indicators/` — what is observed to describe the world state
- `snapshots/` — reproducible frozen inputs
- `universe/` — what is in or out of scope

## Rule of use

Do not collapse person-level, group-level, and geopolitical inputs into one undifferentiated layer.

The system should preserve at least two perspectives throughout the pipeline:
1. the individual person
2. the group or collective

A third layer, geopolitical and institutional structure, may shape both.
