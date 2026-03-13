# IDs, Status, and Versioning in Invest-GT

## Purpose

This file defines the identity, status, and versioning logic for major artifacts in Invest-GT.

Its purpose is to make repository objects stable, referencable, auditable, and reproducible before implementation begins.

Without explicit identity and versioning rules, the repository would quickly become structurally weak:

- hypotheses could change without trace
- scenarios could be discussed without stable references
- models could drift across runs
- reports could not be tied cleanly back to concrete artifacts
- results could be confused across execution contexts

This file exists to prevent that.

---

## Why this matters

Invest-GT is not intended to be a loose note-taking or brainstorming repository.

It is intended to support:

- explicit reasoning
- traceable simulation
- reproducible execution
- auditable outputs
- structured revision over time

That requires stable identity.

If an artifact cannot be clearly identified, its status cannot be assessed reliably.  
If its status cannot be assessed, it cannot be governed.  
If it cannot be governed, it should not be treated as a core repository artifact.

---

## General principle

Every major artifact in Invest-GT must support:

- a stable artifact identity
- a readable type distinction
- an explicit lifecycle status
- a revision or version logic appropriate to its artifact family
- traceable links to upstream and downstream artifacts

Identity is not optional metadata.  
It is part of the artifact structure itself.

---

## Three layers to distinguish

This repository should distinguish clearly between:

### 1. Artifact ID

The stable identity of an artifact as a repository object.

This answers:

> Which artifact is this?

Example:
- `HYP-014`
- `SCN-003`
- `MOD-005`

### 2. Version or revision

The state of that artifact across meaningful change.

This answers:

> Which form of this artifact is this?

Example:
- `HYP-014@v1`
- `HYP-014@v2`
- `SCN-003@v4`

### 3. Run-time reference

The concrete execution-time use of artifacts in a specific run.

This answers:

> Which exact versions were used in this execution?

Example:
- `RUN-20260312-001` uses `HYP-014@v2`, `SCN-003@v1`, and `MOD-005@v3`

These three layers must not be collapsed into one.

---

## Identity model

Each major artifact should eventually have at least the following identity fields:

- `artifact_type`
- `artifact_id`
- `version`
- `status`
- `created_at`
- `updated_at`
- `created_by`
- `supersedes` or `derived_from` where relevant

Depending on implementation, these may appear in:

- YAML front matter
- JSON records
- schema fields
- registries
- manifest files

The storage format can vary.  
The structural requirement should not.

---

## Canonical artifact type prefixes

The following prefixes are recommended for canonical artifact families.

### World-state artifacts
- `SNAP-###`

Example:
- `SNAP-001`
- `SNAP-024`

### Hypothesis artifacts
- `HYP-###`

Example:
- `HYP-001`
- `HYP-014`

### Scenario artifacts
- `SCN-###`

Example:
- `SCN-001`
- `SCN-009`

### Agent artifacts
- `AGT-###`

Example:
- `AGT-001`
- `AGT-007`

### Model artifacts
- `MOD-###`

Example:
- `MOD-001`
- `MOD-005`

### Run artifacts
- `RUN-YYYYMMDD-###`

Example:
- `RUN-20260312-001`
- `RUN-20260312-002`

### Result artifacts
- `RES-YYYYMMDD-###`

Example:
- `RES-20260312-001`

### Report artifacts
- `RPT-YYYYMMDD-###`

Example:
- `RPT-20260312-001`

### Validation artifacts
- `VAL-YYYYMMDD-###`

Example:
- `VAL-20260312-001`

### Dataset or source package artifacts
- `DAT-###`

Example:
- `DAT-003`

These prefixes should remain canonical once adopted.

---

## ID design rules

Artifact IDs should follow these rules.

### Rule 1: IDs are stable

An artifact ID should not change merely because the content evolves.

For example:
- `HYP-014` remains `HYP-014` across revisions
- the version changes, not the ID

### Rule 2: IDs are unique within artifact family

No two hypotheses should share the same `HYP-###` ID.  
No two scenarios should share the same `SCN-###` ID.

### Rule 3: IDs should be opaque enough to remain stable

The ID should not depend too heavily on human-readable titles.

Good:
- `HYP-014`

Risky:
- `HYP-china-industrial-slowdown-leading-to-eu-defense-repricing`

Human-readable slugs can be added separately.

### Rule 4: IDs should be human-usable

IDs should be short enough to appear in:
- discussions
- filenames
- manifests
- reports
- validation records

### Rule 5: Type should be visible from the ID

The artifact family should be obvious from the prefix.

This reduces ambiguity in logs, reports, registries, and execution traces.

---

## Human-readable titles and slugs

Every major artifact may also carry:

- `title`
- `slug`

These are useful, but secondary.

Example:

- `artifact_id: HYP-014`
- `title: Sanctions-driven industrial reallocation toward domestic energy infrastructure`
- `slug: sanctions-industrial-reallocation-energy-infrastructure`

The title and slug may change if clarity improves.  
The artifact ID should remain stable.

---

## Versioning principle

Not every artifact family changes in the same way.

Versioning should be explicit, but proportional to artifact type.

The general recommendation is:

- use integer versions for conceptual artifacts
- use dated execution IDs for run-derived artifacts
- use derivation links where simple version increments are not sufficient

---

## Recommended version format

For major repository artifacts, the default version format should be:

- `v1`
- `v2`
- `v3`

Stored as either:
- `version: 1`
or
- `version: "v1"`

The important point is consistency.

A simple integer-based versioning model is preferable at the start.  
It is clearer than premature semantic versioning.

---

## When to increment a version

A version should be incremented when a change is substantively meaningful.

This includes changes such as:

- altered claim structure
- changed assumptions
- new falsification logic
- changed scenario boundaries
- changed model logic
- changed validation criteria
- materially different output interpretation rules

A version should usually **not** be incremented for purely editorial corrections such as:

- spelling fixes
- formatting cleanup
- non-substantive wording improvements
- corrected links
- metadata normalization without conceptual change

If needed, minor editorial tracking can exist separately, but conceptual versioning should stay readable.

---

## Status model

Every major artifact should carry a status.

Status answers:

> What is the current governance state of this artifact?

Status is distinct from version.

A new version may still be `draft`.  
An older version may remain `archived`.  
A rejected artifact still has an identity and possibly version history.

---

## Recommended base statuses

The following status vocabulary is recommended as a base layer:

- `draft`
- `active`
- `in_review`
- `validated`
- `deprecated`
- `superseded`
- `rejected`
- `archived`
- `invalidated`

Not every artifact family needs every status.

---

## Status meanings

### draft

The artifact exists but is not yet ready for active dependency.

Use when:
- early construction is in progress
- assumptions are incomplete
- validation has not started
- structure is still unstable

### in_review

The artifact is being actively checked or revised and should not yet be treated as settled.

Use when:
- formal review is ongoing
- competing revisions are being compared
- validation is underway

### active

The artifact is available for normal repository use.

Use when:
- it is structurally complete enough
- it may be referenced downstream
- no stronger status has yet been assigned

### validated

The artifact has passed an explicit validation step appropriate to its type.

Use when:
- a defined check has been completed
- the result is documented in validation artifacts

This does not imply absolute truth.  
It means the artifact passed stated validation criteria.

### deprecated

The artifact is still known but should no longer be preferred.

Use when:
- a better replacement exists
- the artifact remains historically relevant
- older runs may still reference it

### superseded

The artifact has been replaced by a newer artifact or newer version.

Use when:
- a successor has been designated explicitly

This should usually be accompanied by:
- `superseded_by`

### rejected

The artifact has been considered and not accepted for active use.

Use when:
- the claim fails
- admissibility is insufficient
- structure is not acceptable
- the artifact should not proceed downstream

### invalidated

The artifact was once active or plausible, but later evidence or checks have broken its standing.

Use when:
- assumptions no longer hold
- provenance failed
- key logic collapsed
- contradiction or falsification occurred

### archived

The artifact is no longer active, but retained for history, traceability, or comparison.

Use when:
- it is no longer current
- it remains worth keeping accessible

---

## Family-specific status guidance

Different artifact families should use status somewhat differently.

### World snapshots

Typical statuses:
- `draft`
- `active`
- `archived`
- `invalidated`

### Hypotheses

Typical statuses:
- `draft`
- `in_review`
- `active`
- `validated`
- `rejected`
- `superseded`
- `invalidated`
- `archived`

### Scenarios

Typical statuses:
- `draft`
- `active`
- `superseded`
- `archived`

### Agents

Typical statuses:
- `draft`
- `active`
- `deprecated`
- `archived`

### Models

Typical statuses:
- `draft`
- `in_review`
- `active`
- `validated`
- `deprecated`
- `superseded`
- `invalidated`
- `archived`

### Runs

Typical statuses:
- `planned`
- `executing`
- `completed`
- `failed`
- `cancelled`

Runs may require a more execution-specific status model than conceptual artifacts.

### Results

Typical statuses:
- `generated`
- `flagged`
- `accepted_for_review`
- `invalidated`
- `archived`

### Reports

Typical statuses:
- `draft`
- `in_review`
- `published`
- `revised`
- `archived`

### Validation records

Typical statuses:
- `open`
- `partial`
- `passed`
- `failed`
- `archived`

These can be refined later, but should remain explicit.

---

## Relationship fields

Artifacts should eventually support explicit relationship fields where useful.

Examples:

- `derived_from`
- `depends_on`
- `linked_to`
- `supersedes`
- `superseded_by`
- `validated_by`
- `invalidated_by`
- `uses_model`
- `uses_scenario`
- `uses_snapshot`

These relations are especially important once the repository has multiple parallel runs and revisions.

---

## Recommended minimum metadata by artifact family

The following minimum metadata is recommended.

### World Snapshot
- `artifact_type`
- `artifact_id`
- `version`
- `status`
- `title`
- `time_reference`
- `scope`
- `created_at`

### Hypothesis
- `artifact_type`
- `artifact_id`
- `version`
- `status`
- `title`
- `claim`
- `created_at`
- `derived_from` or `depends_on`

### Scenario
- `artifact_type`
- `artifact_id`
- `version`
- `status`
- `title`
- `time_horizon`
- `created_at`

### Agent
- `artifact_type`
- `artifact_id`
- `version`
- `status`
- `title`
- `agent_type`
- `created_at`

### Model
- `artifact_type`
- `artifact_id`
- `version`
- `status`
- `title`
- `model_purpose`
- `created_at`

### Run Manifest
- `artifact_type`
- `artifact_id`
- `status`
- `created_at`
- `snapshot_ref`
- `scenario_ref`
- `hypothesis_refs`
- `model_refs`

### Result
- `artifact_type`
- `artifact_id`
- `status`
- `created_at`
- `run_ref`

### Report
- `artifact_type`
- `artifact_id`
- `version`
- `status`
- `title`
- `created_at`
- `run_ref` or `result_ref`

### Validation Record
- `artifact_type`
- `artifact_id`
- `status`
- `created_at`
- `target_refs`
- `validation_type`

---

## Filenames vs artifact IDs

Filenames should not be treated as the primary identity layer.

A file may move, split, or be renamed.  
The artifact ID should remain stable.

Recommended pattern:

- file path and name are for organization
- artifact ID is for identity
- title is for human readability
- slug is for convenience

Example:

File path:
`hypotheses/active/HYP-014-energy-infrastructure-reallocation.md`

Metadata inside:
- `artifact_id: HYP-014`
- `version: v2`
- `title: Sanctions-driven industrial reallocation toward domestic energy infrastructure`

If the filename changes later, the artifact ID should not.

---

## Runs and derived artifacts

Runs and results are special because they are execution-derived.

They should not rely only on conceptual versioning.

### Runs

Runs should have unique execution identities such as:

- `RUN-20260312-001`

This identity should refer to one concrete execution context.

If a run is repeated with changed inputs or settings, it should usually become a new run, not overwrite the old one.

### Results

Results should either:
- carry their own `RES-...` ID
or
- derive deterministically from the run ID

The important point is that results remain attributable to a specific execution context.

---

## Supersession rules

When an artifact is replaced meaningfully, supersession should be explicit.

Recommended fields:
- `supersedes`
- `superseded_by`

Example:

`HYP-014@v3`
- `supersedes: HYP-014@v2`

Or, if a new artifact replaces an older one conceptually:

`HYP-031@v1`
- `supersedes: HYP-014@v3`

This matters because not every replacement is just a new version of the same artifact.  
Sometimes the conceptual object itself changes.

---

## Rejection and invalidation rules

The repository should distinguish between:

### rejected

The artifact should not be promoted or used because it failed before acceptance.

### invalidated

The artifact was once active or admissible enough to matter, but later lost standing.

This distinction is important for historical traceability.

A rejected artifact tells us:
- it was considered, but not admitted

An invalidated artifact tells us:
- it once mattered, but later broke

These are epistemically different states.

---

## Auditability rule

A reviewer should be able to answer all of the following for any major artifact:

- What is its stable ID?
- What version is being used?
- What is its current status?
- What did it derive from?
- What does it supersede, if anything?
- Which downstream artifacts depend on it?
- Was it validated, rejected, deprecated, or invalidated?

If the answer to these questions is missing, the artifact is under-governed.

---

## Recommended directory implications

This identity system suggests future repository structures such as:

- `registry/hypotheses.yaml`
- `registry/scenarios.yaml`
- `registry/models.yaml`
- `registry/runs.yaml`
- `registry/reports.yaml`

and/or artifact-local metadata in files such as:

- `hypotheses/active/HYP-014-...md`
- `scenarios/SCN-003-...yaml`
- `models/MOD-005-...md`
- `simulations/manifests/RUN-20260312-001.yaml`

The exact storage approach can vary.  
What matters is that the identity logic stays canonical.

---

## What this file does not define

This file defines the logic of identity, status, and versioning.

It does not yet define:

- the full artifact schemas
- registry implementation details
- how IDs are generated operationally
- stage-specific contracts
- run configuration structure
- validation methodology

These should be specified separately.

---

## Status of this file

This file is canonical for:

- artifact ID logic
- artifact status logic
- versioning expectations
- supersession and invalidation distinctions

Any new major artifact type introduced into the repository should either:

- follow these rules directly, or
- document a justified exception explicitly
