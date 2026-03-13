# Invest-GT within the Finkeissen Research Architecture

## Purpose

This repository is not intended to be interpreted as a standalone system in a vacuum.

It is part of the broader [finkeissen](https://github.com/finkeissen) research architecture and should be understood within that larger epistemic and infrastructural context.

The repositories together form one pipeline and must be interpreted together.

Invest-GT is therefore embedded in a wider architecture for truth-seeking, admissibility control, auditable reasoning, and constrained knowledge production.

---

## Central framing

The broader architecture can be described as a:

- maximally truth-seeking pipeline for reliable and auditable AI
- central entry point to the Ekkehard Finkeissen research architecture
- coherent and constraint-based epistemic framework
- infrastructure for auditable knowledge and decision systems

This architecture is designed around one core principle:

> Any statement not explicitly bound to a concrete problem context is treated as epistemically inadmissible. Processing stops.

This means admissibility is not an optional quality criterion added after generation.  
It is a hard precondition for further processing.

Modern AI systems frequently produce claims without explicit epistemic binding.  
The purpose of the larger architecture is to counter this by enforcing context-bound admissibility as a structural constraint.

---

## Core principle

The architecture is built around epistemic admissibility.

A claim is not acceptable merely because it is coherent, plausible, fluent, or useful.  
A claim must be bound to an explicit context, traceable to its originating conditions, and processable under explicit admissibility constraints.

If that binding cannot be established, the artifact is not upgraded.  
It is stopped, rejected, or moved into a legacy state.

This makes admissibility precede claims.

---

## What this architecture is not

The broader architecture is explicitly **not**:

- a prompt framework
- an absolute or unquestionable knowledge base
- an LLM wrapper

It is instead a constraint architecture for epistemic governance.

---

## Research areas

The broader architecture touches at least the following research areas:

- epistemic governance
- epistemic admissibility
- constraint-based reasoning
- knowledge provenance
- AI safety
- hallucination mitigation
- scientific workflows for AI
- verification of claims
- formal reasoning for LLM systems
- auditable decision systems

---

## Cyclical pipeline

The architecture is cyclical rather than purely linear.

Artifacts can move forward when admissibility conditions are met.  
They can also regress into legacy states when admissibility fails, provenance breaks, or unresolved contradictions remain.

In this sense, the architecture is a governance loop, not a one-way production pipeline.

Examples and concrete artifact forms can be explored in the related repositories, especially the Matrix repository.

---

## Architectural steps

### Step 0 – Legacy

Active sink for inadmissible, unresolved, inconsistent, or insufficiently grounded artifacts.

Repository: [legacy](https://github.com/finkeissen/legacy)

Legacy is not merely archival storage.  
It functions as an explicit epistemic sink for artifacts that cannot currently be admitted into the active system.

---

### Step 1 – Research-Program

Epistemic admissibility rules, STOP conditions, and core grammar.

Repository: [research-program](https://github.com/finkeissen/research-program)

This is the conceptual and normative starting point of the architecture.  
It defines the admissibility regime under which all downstream artifacts must operate.

---

### Step 2 – Matrix-Management-System (MMS)

Constraint execution layer enforcing epistemic governance across artifacts.

Repository: [mms](https://github.com/finkeissen/mms)

MMS operationalizes the admissibility logic and applies governance constraints to artifacts moving through the architecture.

If admissibility fails, processing stops and the artifact may be routed to Legacy.

---

### Step 3 – Matrix

Matrix registers admissible knowledge artifacts together with their originating context.

Repository: [matrix](https://github.com/finkeissen/matrix)

The Matrix is not a generic database of claims.  
It is a structured register of admissible artifacts with explicit contextual binding.

This repository is especially important for understanding examples of admissibility, artifact registration, and traceable knowledge handling.

---

### Step 4 – Hypotheses

Versioned, falsifiable claims derived from the epistemic core.

Repository: [hypotheses](https://github.com/finkeissen/hypotheses)

Hypotheses are not free-floating ideas.  
They are constrained, versioned, and expected to remain falsifiable and context-bound.

If they fail admissibility checks, they are not promoted and may be routed to Legacy.

---

### Step 5 – Predictions

Operationally verifiable projections derived from hypotheses and matrix.

Repository: [predictions](https://github.com/finkeissen/predictions)

Predictions are the operational layer in which constrained hypotheses are transformed into testable forward-looking claims.

---

### Step 6 – The LIFE Art Framework

Framework and art projects about life — grounded in the research-program, yet not formally bound in the same way as the core epistemic repositories.

Repository: [life](https://github.com/finkeissen/life)

This layer is related to the broader architecture, but differs in its degree of formal binding.  
Contributions are welcome if they operate under the architectural constraints of that repository and its license terms.

---

## Where Invest-GT sits

Invest-GT should be interpreted as a domain-specific downstream research and simulation repository within this broader architecture.

Its role is not to replace the epistemic core repositories.  
Its role is to apply their discipline to the domain of investment-relevant world modeling, hypothesis formation, simulation, and allocation-oriented reasoning.

In other words:

- the broader architecture defines admissibility, governance, provenance, and epistemic constraints
- Invest-GT applies those constraints within a specific domain of inquiry

This means Invest-GT must not silently relax the standards established upstream.

---

## Consequences for this repository

Because Invest-GT is embedded in the larger architecture, the following expectations apply:

1. No claim should be treated as admissible merely because it appears plausible.
2. Every meaningful artifact should remain context-bound and traceable.
3. Hypotheses should remain explicit, versioned, and falsifiable.
4. Simulations should be reproducible and auditable.
5. Outputs that fail admissibility or traceability requirements should not be normalized as valid results.
6. The repository should be read as one constrained component within a larger epistemic pipeline.

---

## Reading guidance

To understand this repository correctly, it should be read together with the broader architecture, especially:

- `research-program` for admissibility rules and STOP conditions
- `mms` for governance and execution constraints
- `matrix` for registered admissible artifacts and contextual binding
- `hypotheses` for versioned falsifiable claim structures
- `predictions` for operational projection logic

Invest-GT is therefore best understood not as an isolated project, but as a domain-specific implementation space inside the larger Finkeissen research architecture.

---

## Status note

This file defines architectural embedding and interpretive context.

It does **not** replace repository-local documentation such as:

- scope
- pipeline design
- domain assumptions
- simulation structure
- validation procedures

Those remain repository-specific and must be defined separately.
