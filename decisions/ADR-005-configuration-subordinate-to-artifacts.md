# ADR-005: Configuration Remains Subordinate to Canonical Artifacts

## Status

Accepted

---

## Date

2026-03-12

---

## Context

Invest-GT is being developed as an artifact-governed, constraint-bound pipeline repository.

Earlier architectural decisions established that:

- canonical repository meaning should live in governed artifacts rather than hidden implementation state
- human exploratory work must remain distinct from canonical repository layers
- reproducibility depends on explicit snapshots and run manifests
- validation and evaluation must function as first-class governance layers

Within that architecture, configuration is unavoidable.

The repository will need configuration for matters such as:

- runtime mode
- parameter selection
- output handling
- validation strictness
- report rendering behavior
- environment-specific technical settings
- execution-specific overrides

However, configuration is also one of the most common sources of structural drift.

In repositories of this kind, conceptual meaning often ends up migrating into configuration through patterns such as:

- scenarios being defined mainly through flags rather than explicit scenario artifacts
- model assumptions being encoded only in parameter files with no model-level documentation
- validation thresholds becoming hidden methodology
- local machine defaults silently altering run meaning
- report behavior changing interpretive claims via rendering options or summary defaults
- run comparability collapsing because effective configuration cannot be reconstructed

A clear architectural decision is therefore needed:

How should configuration relate to canonical artifacts and repository meaning?

---

## Decision

Invest-GT will treat **configuration as subordinate to canonical artifacts**.

Configuration may shape execution behavior, but it must not silently become the repository's hidden conceptual layer.

The core rule is:

> if a change materially alters the meaning of a canonical artifact or the interpretation of a run, that change must not live only in configuration

This means:

1. canonical artifacts define repository meaning
2. configuration defines bounded operational behavior around those artifacts
3. materially meaningful configuration must be explicit, referenceable, and reproducible
4. local or environment-specific settings must not silently change conceptual run meaning
5. important overrides must be visible in run manifests or equivalent governed records

Configuration is therefore legitimate and necessary, but it is not allowed to outrank the artifact layer.

---

## Interpretation

This decision does **not** reject configuration.

It rejects the pattern in which configuration becomes the hidden source of truth.

A strong configuration layer should:

- support explicit operational choice
- preserve reproducibility
- remain reconstructable
- keep override behavior legible
- stay separate from artifact identity and artifact meaning

The repository therefore adopts the following hierarchy:

1. architecture decisions
2. artifact definitions
3. stage contracts
4. governed input and snapshot state
5. canonical artifact selection
6. configuration of execution details

Configuration comes late in that chain.

---

## Why this decision is necessary

Without an explicit rule, configuration tends to absorb conceptual responsibility because it is convenient.

That creates several predictable failure modes.

### Failure mode 1: hidden theory in settings

Scenario meaning, model meaning, or report logic gradually migrates into config files, so the real architecture becomes hard to inspect.

### Failure mode 2: irreproducible runs

A run manifest references artifacts, but the effective configuration depends on defaults, local files, or overrides that were never captured clearly.

### Failure mode 3: weak comparison

Two runs appear comparable on paper, but hidden config differences make the outputs semantically different.

### Failure mode 4: local environment as silent driver

Machine-local config changes what the repository effectively does without any canonical visibility.

### Failure mode 5: methodological drift through thresholds

Interpretation-relevant thresholds or aggregation choices drift operationally and become hidden method changes.

This ADR exists to prevent those outcomes.

---

## What this decision allows

Configuration is valid for bounded concerns such as:

- runtime mode selection
- parameter profiles
- logging intensity
- output persistence
- report rendering profiles
- validation profile selection
- machine-local technical paths
- cache handling
- non-conceptual performance settings

These are legitimate configuration concerns when they remain explicit and appropriately governed.

---

## What this decision forbids

Configuration must not be the only place where the following live:

- canonical hypothesis content
- canonical scenario meaning
- model identity
- epistemically load-bearing assumptions
- hidden methodological choices that materially affect interpretation
- silent environment-specific changes to run meaning
- report-supporting logic that cannot be reconstructed from governed artifacts and referenced config

If a setting materially changes what the repository is saying rather than how it is operating, then that setting is too important to live only as config.

---

## Consequences

### 1. Important configuration becomes governable

Material configuration should be identifiable, referenceable, and, where necessary, version-visible.

This is especially important for:

- model parameter profiles
- scenario execution profiles
- validation profiles
- reporting profiles

### 2. Run manifests must capture effective configuration

A materially important run must not depend on invisible config state.

The run manifest should therefore capture or reference:

- the config used
- the config version where relevant
- any material overrides
- any non-default execution settings that affect interpretation or reproducibility

### 3. Environment-local settings remain constrained

Local technical settings may exist, but they must not silently alter conceptual meaning.

Examples of acceptable environment-local concerns include:

- filesystem paths
- caches
- local resource controls
- secrets or credentials, where relevant later

Examples of unacceptable hidden environment-local influence include:

- selecting a different active scenario implicitly
- weakening validation gates for report-supporting runs
- changing key interpretation thresholds with no manifest visibility

### 4. Defaults become explicit design choices

Defaults are not neutral.

If a default materially affects behavior, it must be visible and documented.

"It used the default" must remain a reconstructable statement, not a vague excuse.

### 5. Methodological decisions cannot hide in config alone

If a choice is methodologically load-bearing, it should also appear in the appropriate conceptual layer such as:

- model specification
- validation documentation
- report logic
- architecture decision records

Operational encoding in config is allowed. Exclusive existence in config is not.

---

## Distinction between artifact meaning and execution shaping

This ADR depends on a clear distinction.

### Artifact meaning

Examples:

- what a hypothesis claims
- what a scenario structurally represents
- what a model is meant to do
- what a snapshot includes
- what a report is entitled to conclude

### Execution shaping

Examples:

- deterministic vs stochastic mode
- parameter selection within a defined model family
- logging verbosity
- report formatting depth
- selected validation profile

Configuration is appropriate mainly for execution shaping.

When a setting begins to alter artifact meaning, it crosses the line into the canonical layer.

---

## Override rule

Overrides are allowed only if the override chain remains legible.

A reviewer should be able to answer:

- what was the baseline configuration?
- what was overridden?
- where was it overridden?
- why was it overridden?
- did the override materially affect interpretation?

If that cannot be answered, the override system is too opaque for this repository architecture.

---

## Recommended override order

The repository should conceptually distinguish an override order such as:

1. repository defaults
2. artifact-family config
3. scenario- or model-specific config
4. run-referenced config
5. explicit run-local override
6. environment-local technical settings

The exact implementation may evolve, but override precedence must be explicit.

An unstructured tangle of implicit overrides is incompatible with this ADR.

---

## Relation to run manifests

This ADR is closely tied to ADR-003.

Snapshots preserve governed input state.
Run manifests preserve governed execution binding.

Configuration sits inside that reproducibility core only when it is made explicit through the run-manifest layer.

This means:

- a materially important run should reveal its effective configuration
- a run comparison should not rely on guessed defaults
- reruns should not quietly inherit changed settings with no visibility

Run manifests are therefore the main place where configuration becomes reproducibly accountable.

---

## Relation to validation and evaluation

Configurations may themselves require checking.

Relevant validation questions include:

- is the configuration structurally complete?
- does it violate a stage contract?
- does it contradict the selected model or scenario?
- does it introduce ambiguous override logic?
- does it weaken review intensity inappropriately?
- does it change interpretive behavior in a way that should block progression?

This ADR therefore implies that configuration is not "just technical." It is part of repository governance when it matters materially.

---

## What this decision rejects

### Rejected alternative 1: configuration as the real execution truth

This was rejected because it would make conceptual meaning too easy to hide and too hard to review.

### Rejected alternative 2: local config is acceptable as operational memory

This was rejected because it creates hidden state and weakens reproducibility.

### Rejected alternative 3: defaults do not need governance

This was rejected because defaults often carry real interpretive weight.

### Rejected alternative 4: methodology can live in config alone

This was rejected because load-bearing methodological choices should remain visible in conceptual documentation and governed artifacts.

### Rejected alternative 5: a run manifest can omit effective config if the codebase is stable

This was rejected because stable code does not guarantee stable effective behavior.

---

## Trade-offs

This decision has costs.

### Cost 1: more explicit configuration management

Important configs must be documented, referenced, and sometimes versioned.

### Cost 2: less tolerance for convenient hidden defaults

Developers and researchers must surface more of what would otherwise remain implicit.

### Cost 3: more discipline around overrides

Ad hoc experimentation may require more explicit handling if it becomes canonically relevant.

These costs are accepted because they buy:

- stronger reproducibility
- stronger run comparison
- better auditability
- less hidden methodology
- clearer separation of conceptual and operational concerns

---

## Practical implications

This ADR implies several structural directions.

### Dedicated config layer

The repository should maintain an explicit `configs/` layer rather than scattering settings arbitrarily.

### Separation between canonical and local config

Environment-local technical settings should remain separate from repository-canonical settings.

### Config references in manifests

Run manifests should capture or reference material configuration.

### Config visibility in review

Important config differences should be visible during run review, comparison, validation, and reporting.

### Potential future config IDs or versions

Material configuration profiles may need stable references if they become reused or compared over time.

---

## Review rule

A useful architectural review question is:

> if this config file, default, or local override changed silently, would the repository mean something different in a way that a reviewer should care about?

If the answer is yes, then the relevant behavior is too important to remain invisible or purely local.

---

## Compatibility with lightweight implementation

This ADR does **not** require a heavy configuration system from the start.

A lightweight implementation may still satisfy it using:

- a small `configs/` tree
- explicit config refs in run manifests
- simple YAML files
- a documented override order
- clear separation between canonical and local settings

The architectural requirement is not complexity. It is governed visibility.

---

## Non-goals of this decision

This decision does **not** yet define:

- final config schemas
- exact file formats
- config loading implementation
- CLI flag behavior
- environment provisioning
- secret management
- automatic config resolution tooling

These may be decided later.

This ADR defines how configuration must relate to canonical artifacts, not the full technical implementation.

---

## Relation to earlier ADRs

This ADR builds directly on:

- ADR-001: repository architecture is artifact-governed and constraint-bound
- ADR-002: human exploratory layers must remain distinct from canonical layers
- ADR-003: snapshots and run manifests form the reproducibility core

ADR-005 adds the rule that configuration may shape execution, but must remain subordinate to canonical artifact meaning.

---

## Summary

Invest-GT will treat configuration as subordinate to canonical artifacts.

This means:

- artifacts define repository meaning
- configuration defines bounded operational behavior
- important config must be explicit and reconstructable
- local settings must not silently change conceptual meaning
- materially important runs must make effective configuration visible

This decision is necessary to prevent configuration from becoming the repository's hidden theory layer.
