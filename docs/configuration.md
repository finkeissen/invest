# Configuration in Invest-GT

## Purpose

This file defines the role, boundaries, and governance logic of configuration in Invest-GT.

Configuration is the layer that makes repository behavior operationally selectable without silently changing the meaning of canonical artifacts.

In this repository, configuration is necessary because the same general architecture may need to support:

- different scenarios
- different runtime modes
- different model selections
- different parameter settings
- different output behaviors
- different validation intensities
- different exploratory or report-supporting execution contexts

At the same time, configuration is dangerous if it becomes an ungoverned place where major conceptual changes are smuggled in through technical convenience.

This file is canonical for configuration logic.

---

## Why configuration matters

A repository like Invest-GT can fail structurally if configuration is handled informally.

Typical failure modes include:

- hidden defaults changing run meaning
- scenario logic partially encoded in config and partially encoded in artifacts
- model assumptions living only in runtime flags
- runs becoming irreproducible because config state is not preserved
- exploratory overrides being mistaken for canonical settings
- report-supporting runs depending on ad hoc local changes
- the same run manifest meaning different things on different machines

Configuration exists to make operational choice explicit.  
But it must remain governed.

---

## Core principle

Configuration may influence execution.  
It must not silently replace explicit artifacts.

That means configuration is allowed to control things such as:

- runtime mode
- execution options
- parameter values
- output behavior
- validation strictness
- non-conceptual thresholds
- toggles for bounded operational choices

But configuration should not become the hidden place where the repository's real conceptual structure lives.

A strong rule is:

> if a change materially alters the meaning of a core artifact, it should be reflected in the artifact layer, not only in configuration

---

## What configuration is

Configuration is a governed specification of operational settings that shape how artifacts are bound, executed, checked, or rendered.

A configuration may define things such as:

- which execution mode to use
- which optional modules are active
- which thresholds apply
- which parameter set is used
- how outputs are stored
- what logging intensity applies
- what validation gates are required
- which comparison mode is active

Configuration is therefore operational and structural, but not identical to the artifact model itself.

---

## What configuration is not

Configuration is not:

- a scenario
- a hypothesis
- a world snapshot
- a model specification
- a run manifest
- a report
- a substitute for versioned artifacts
- a hidden theory layer

These distinctions matter because configuration often drifts into conceptual overload if not constrained.

---

## Why configuration is risky

Configuration is one of the easiest places for structural drift to enter a repository.

This happens when:

- defaults become invisible assumptions
- local machine state overrides repository behavior
- conceptual choices hide inside technical flags
- config changes are not versioned or referenced
- runs become non-comparable due to unrecorded overrides
- scenario differences are implemented as config mutations rather than explicit scenario artifacts

This file exists to keep configuration explicit and subordinate to the artifact architecture.

---

## Configuration must remain subordinate to artifacts

The repository should preserve the following hierarchy:

1. architectural principles
2. artifact definitions
3. stage contracts
4. governed input state
5. explicit artifact selection
6. configuration of execution details

Configuration belongs below artifact identity and below artifact meaning.

A configuration may tell the repository how to execute a selected model.  
It should not decide, invisibly, which model conceptually exists.

A configuration may choose a threshold.  
It should not silently replace a hypothesis.

---

## What configuration should be used for

Configuration is appropriate for repository choices such as:

### 1. Runtime behavior

Examples:
- deterministic vs stochastic mode
- batch vs single-run execution
- logging intensity
- output persistence settings

### 2. Parameter sets

Examples:
- model parameter values
- sensitivity ranges
- simulation horizon granularity
- perturbation levels

### 3. Validation settings

Examples:
- required validation gates
- strictness levels
- review intensity mode
- whether exploratory runs may skip certain non-critical checks

### 4. Output settings

Examples:
- report rendering mode
- serialization format
- storage paths
- summary verbosity mode

### 5. Environment-specific technical settings

Examples:
- local output directory
- cache location
- resource constraints
- machine-specific technical paths

These can be legitimate config concerns if handled cleanly.

---

## What configuration should not be used for

Configuration should not silently encode things such as:

### 1. The content of canonical hypotheses

A hypothesis should exist as a governed artifact, not as a config switch with hidden claim logic.

### 2. The conceptual meaning of a scenario

A scenario may be selected by config, but it should not exist only as a loose set of flags.

### 3. The identity of core artifacts

Artifact identity belongs in registries, manifests, and canonical metadata, not in fragile local config assumptions.

### 4. Undocumented methodological decisions

If a methodological choice matters structurally, it should be documented in specs, models, contracts, or decisions.

### 5. Epistemically load-bearing assumptions hidden as technical defaults

If a default materially changes interpretation, it is not "just config."

---

## Main configuration goals

A strong configuration layer should support at least:

- reproducibility
- explicitness
- bounded operational flexibility
- separation of conceptual and operational concerns
- controlled overrides
- auditability
- comparability across runs

If the configuration system makes these worse, it is too loose.

---

## Recommended configuration layers

A useful structure for this repository is to distinguish several layers of configuration.

Recommended conceptual layers:

1. defaults
2. artifact-linked configs
3. scenario-specific configs
4. runtime configs
5. run-local overrides
6. environment-local technical settings

These layers should not be collapsed into one giant file.

---

# 1. Defaults

## Purpose

Defaults define the normal baseline operational behavior of the repository.

They should be conservative, explicit, and safe enough that a run does not accidentally depend on undocumented local assumptions.

## Examples

- default logging level
- default output conventions
- default validation expectations
- default storage behavior
- default runtime flags that do not alter conceptual meaning

## Governance rule

Defaults should never contain hidden conceptual commitments that materially change the interpretation of canonical artifacts.

---

# 2. Artifact-linked configs

## Purpose

Some configurations may be naturally associated with specific artifact families.

Examples:
- model parameter templates
- scenario execution settings
- report rendering profiles
- validation criteria bundles

## Governance rule

If a config is materially tied to an artifact family, that linkage should remain explicit.

Example:
- a model may reference a parameter profile
- a run manifest may reference a scenario execution config
- a report may reference a rendering profile

This is stronger than relying on global implicit defaults.

---

# 3. Scenario-specific configs

## Purpose

Some execution settings may be tied naturally to a scenario.

Examples:
- time-step choices
- actor activation sets
- branch handling options
- policy shock variants
- sensitivity ranges relevant to that scenario

## Governance rule

Scenario-specific config may shape how a scenario is executed, but should not replace the scenario artifact itself.

If the scenario meaning changes materially, the scenario should change too.

---

# 4. Runtime configs

## Purpose

Runtime configs govern execution behavior.

Examples:
- deterministic vs stochastic mode
- parallelization settings
- seed behavior
- iteration count
- logging detail
- output retention

## Governance rule

Runtime configs are often legitimate, but they should be captured in or referenced by the run manifest when material.

A run should not rely on invisible local runtime state.

---

# 5. Run-local overrides

## Purpose

A specific run may need a bounded override relative to normal defaults.

Examples:
- one sensitivity threshold changed
- one validation gate tightened
- one output mode enabled
- one parameter set perturbed

## Governance rule

Run-local overrides are acceptable only if:

- they are explicit
- they are bounded
- they are captured in the run manifest or linked config
- they do not silently redefine the conceptual artifacts themselves

Run-local overrides should be treated as notable, not casual.

---

# 6. Environment-local technical settings

## Purpose

Some settings are machine- or operator-specific and do not belong in canonical repository behavior.

Examples:
- local filesystem paths
- cache directories
- temporary output paths
- machine resource settings
- local secrets or credentials, where relevant later

## Governance rule

Environment-local technical settings should be kept separate from canonical repository config.

They must not determine conceptual run meaning.

---

## Recommended configuration directory

**Recommended directory:** `configs/`

A useful initial structure could be:

- `configs/defaults/`
- `configs/scenarios/`
- `configs/models/`
- `configs/runtime/`
- `configs/reports/`
- `configs/validation/`
- `configs/local/`

This structure can evolve, but the separation of concerns should remain.

---

## Recommended file philosophy

At this stage, the repository should aim for:

- a small number of clear config files
- explicit naming
- minimal hidden inheritance
- readable override order
- explicit references from manifests where material

The repository should avoid:

- giant catch-all config blobs
- implicit cascading so complex that reviewers cannot reconstruct actual settings
- undocumented local patches
- silent fallback chains that hide effective behavior

Simplicity is more valuable than configurability for its own sake.

---

## Configuration identity

Important configuration artifacts should themselves be identifiable.

This does not necessarily require full artifact-family treatment from day one, but material configs should be referenceable.

Useful fields may include:

- `config_id`
- `config_type`
- `title`
- `status`
- `version`
- `created_at`
- `updated_at`
- `scope`
- `linked_artifact_refs`

This is especially useful for:
- model parameter configs
- scenario execution configs
- validation profiles
- report rendering configs

The more a config matters, the more it should behave like a governed artifact.

---

## Configuration status

Important configs may also need explicit status.

Possible statuses include:

- `draft`
- `active`
- `deprecated`
- `superseded`
- `archived`

This is particularly helpful once multiple parameter profiles or validation profiles exist.

---

## Configuration versioning

Material configuration changes should be version-visible when they affect run meaning.

Examples of changes that may warrant new version visibility:

- changed parameter ranges
- changed runtime mode defaults
- changed threshold values with interpretive significance
- changed validation requirements
- changed output aggregation rules

Minor editorial cleanup usually does not require full version change.

The main question is:

> would a downstream reviewer consider the effective run behavior materially different?

If yes, the config change should be version-visible or run-explicit.

---

## Configuration references in run manifests

A run manifest should not simply assume a configuration state.

It should reference:

- the config used
- the relevant config version
- any run-local overrides
- any non-default execution settings that materially matter

This is one of the main mechanisms that makes runs reproducible.

See also `docs/run-manifests.md`.

---

## Override principle

Overrides are allowed only when the override chain remains legible.

A reviewer should be able to answer:

- what was the baseline config?
- what was overridden?
- where was it overridden?
- why was it overridden?
- did the override materially affect interpretation?

If this cannot be answered, the override system is too opaque.

---

## Recommended override order

A good conceptual order is:

1. repository defaults
2. artifact-family config
3. scenario- or model-specific config
4. run-referenced config
5. explicit run-local override
6. environment-local technical settings

The lower level may refine the higher level, but should not silently replace repository meaning.

This order can be adjusted later, but an explicit precedence rule is essential.

---

## Hard rule on environment-local settings

Environment-local settings must not be allowed to change conceptual meaning invisibly.

For example, local machine config should not silently alter:

- active scenario selection
- active hypothesis set
- model choice
- validation strictness for report-supporting runs
- interpretation-relevant thresholds without manifest visibility

Environment-local settings should be limited to technical concerns unless explicitly surfaced.

---

## Defaults must be visible

One of the most common configuration failures is invisible defaults.

The repository should therefore avoid situations where:

- "it used the default" means no one knows what actually happened
- default thresholds are not documented
- default output filtering changes interpretive meaning
- default validation behavior differs across contexts without visibility

A default is still a decision.  
It should remain inspectable.

---

## Configs and methodological decisions

Some choices look like config choices but are really methodological decisions.

Examples:
- how uncertainty is aggregated
- what counts as a validation pass
- how actor behavior is abstracted
- which failure modes are represented
- how scenario branching is defined

These may appear in config files operationally, but they should also be documented in the appropriate conceptual layer:

- contracts
- model specs
- validation docs
- decisions

Config should not be the only place they live.

---

## Configs and artifact families

Different artifact families may need different config styles.

### Models

May need:
- parameter profiles
- training or calibration settings
- update rule settings
- sensitivity ranges

### Scenarios

May need:
- branch options
- execution horizon settings
- actor activation patterns
- event injection settings

### Reports

May need:
- rendering profiles
- summary depth
- appendix inclusion mode
- audience-specific formatting profiles

### Validation

May need:
- gate strictness
- required checks
- robustness sweep settings
- comparison baseline selection

These are legitimate, but should stay linked to the appropriate artifact family.

---

## Configs and reproducibility

A repository run is only reproducible if materially relevant config state is reproducible too.

This means:

- configs used in a run must be identifiable
- effective overrides must be visible
- configuration drift must not be silent
- changed configs must not retroactively blur historical runs

If a historical run cannot be reproduced because the effective config is unknown, the run is under-governed.

---

## Configs and comparison

Configuration clarity is especially important for comparisons.

When comparing runs, a reviewer should be able to tell:

- whether differences came from scenario changes
- whether differences came from model changes
- whether differences came from config changes
- whether differences came from random variation
- whether differences came from environment-local behavior

Comparison without configuration visibility is often misleading.

---

## Configs and validation

Configurations themselves may require validation.

Relevant questions may include:

- Is the config structurally complete?
- Does it violate a stage contract?
- Does it request impossible combinations?
- Does it contradict the selected model spec?
- Does it weaken required validation gates improperly?
- Does it introduce ambiguous override logic?

A config should not be treated as harmless merely because it is "just settings."

---

## Stop conditions for configuration

Processing should stop, fail, or downgrade if material configuration problems exist, such as:

- effective config cannot be reconstructed
- override chain is ambiguous
- local environment changes conceptual meaning
- selected config contradicts model or scenario contracts
- defaults are load-bearing but undocumented
- run-local override is materially important but unrecorded
- validation requirements are silently weakened
- multiple config sources conflict without an explicit precedence rule

Configuration is not neutral if it changes meaning invisibly.

---

## Recommended minimal metadata for important configs

Where config artifacts are material, they should ideally support:

- `config_id`
- `config_type`
- `title`
- `status`
- `version`
- `scope`
- `created_at`
- `updated_at`
- `linked_artifact_refs`
- `default_base_ref` where relevant
- `override_notes`
- `validation_notes`

This may later become a formal schema.

---

## Review questions for configuration

Before a configuration setup is treated as strong enough for important runs, the following questions should be answerable:

- What does this config control?
- What does it not control?
- Which defaults are in force?
- Which values are overridden?
- Which overrides materially matter?
- Which artifact families is this config linked to?
- Does it change conceptual meaning or only execution behavior?
- Can a reviewer reconstruct the effective config used in a run?
- Are environment-local settings safely separated?

If these questions cannot be answered, the configuration layer is too weak.

---

## Suggested canonical references

This file should be interpreted together with:

- `docs/artifacts.md`
- `docs/contracts.md`
- `docs/ids-and-versioning.md`
- `docs/run-manifests.md`
- `docs/validation-and-evaluation.md`

These files define the artifact, contract, identity, run, and review context within which configuration operates.

This file specializes that logic for operational settings and override control.

---

## Recommended future directory examples

A possible future structure could be:

- `configs/defaults/runtime.yaml`
- `configs/defaults/reporting.yaml`
- `configs/models/MOD-005-defaults.yaml`
- `configs/scenarios/SCN-003-execution.yaml`
- `configs/validation/standard-review.yaml`
- `configs/reports/executive-summary.yaml`
- `configs/local/example.local.yaml`

This is only illustrative.

The architectural requirement is not a specific tree, but disciplined separation.

---

## Consequences for repository design

This file implies structural additions such as:

- a dedicated `configs/` directory
- explicit separation between canonical and local config
- explicit override rules
- config references in run manifests
- identifiable material config artifacts
- validation of config compatibility
- protection against hidden environment-driven drift

The repository does not need to implement all of this immediately.  
But it should avoid letting configuration become the place where the real logic hides.

---

## What this file does not define

This file defines the conceptual governance of configuration.

It does not yet define:

- exact config schemas
- final file formats
- implementation-specific config loaders
- CLI flag behavior
- secret management
- environment provisioning
- automation for config resolution

Those should be defined separately if implementation requires them.

---

## Status of this file

This file is canonical for:

- what configuration is allowed to do
- what configuration must not silently do
- configuration layering
- override logic
- configuration's relation to runs, artifacts, and reproducibility

Any future configuration system in this repository should either:

- follow this logic directly, or
- document explicitly why an equivalent mechanism is being used instead
