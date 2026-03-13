# Reports in Invest-GT

## Purpose

This file defines the role, structure, and governance logic of reports in Invest-GT.

Reports are the repository's primary interpretive and communicative artifacts.

They translate governed artifact chains into forms that can be reviewed, compared, discussed, archived, and, where appropriate, used for decision support.

A report is therefore not just a presentation layer and not just a narrative convenience.

It is a governed artifact that must remain tied to:

- explicit scope
- explicit upstream artifacts
- explicit uncertainty
- explicit limitations
- explicit validation status

Without this discipline, reports become the place where traceability, admissibility, and epistemic care are most easily lost.

This file is canonical for report logic.

---

## Why reports matter

Invest-GT is not intended to stop at raw inputs, hypotheses, scenarios, or execution outputs.

At some point, the repository must produce interpretable outputs that answer questions such as:

- What was examined?
- What happened in the run?
- Which hypotheses mattered?
- What conclusions are currently supportable?
- How robust are those conclusions?
- What remains uncertain?
- What should a reviewer or decision-maker take away from this artifact chain?

Reports exist to answer such questions in a structured way.

But this communicative step is also risky.

Many repositories lose rigor at exactly this point because reports tend to:

- overcompress uncertainty
- overstate conclusions
- blur input, result, and interpretation
- hide assumptions for readability
- detach claims from the artifacts that support them

This file exists to prevent that.

---

## What a report is

A report is a governed interpretive artifact built from an explicit upstream artifact chain.

A report should synthesize and communicate the meaning of an artifact path such as:

- snapshots
- world snapshots
- hypotheses
- scenarios
- agents
- models
- run manifests
- results
- validation records

A report may contain interpretation, comparison, prioritization, and summary.

But it must remain reconstructable in relation to those upstream artifacts.

---

## What a report is not

A report is not:

- a raw result dump
- a source substitute
- an unconstrained essay
- a free-floating forecast
- a detached executive summary with no artifact lineage
- a justification device for weak upstream work
- an excuse to remove uncertainty because narrative flow feels better

These distinctions are essential.

A report is downstream of the governed artifact chain.  
It must not pretend to be upstream evidence.

---

## Core principle

A report may simplify presentation.  
It may not simplify away epistemically material structure.

That means a report may make the artifact chain easier to understand, but it must not:

- erase important caveats
- hide uncertainty
- suppress failure conditions
- blur validation status
- silently upgrade speculative outputs into settled conclusions

Interpretive clarity is allowed.  
Interpretive distortion is not.

---

## Why reports are difficult

Reports sit at the point where several tensions meet:

- clarity vs completeness
- usefulness vs caution
- synthesis vs compression
- interpretation vs overreach
- decision relevance vs epistemic humility

A weak report usually fails by resolving these tensions invisibly.

A strong report keeps them visible and governed.

---

## Main purposes of reports

Reports in this repository may serve several legitimate purposes.

### 1. Interpretation

Making the meaning of artifact chains intelligible.

### 2. Comparison

Comparing scenarios, hypotheses, runs, or outputs.

### 3. Review support

Helping reviewers inspect what happened and what should be questioned.

### 4. Decision support

Providing bounded, caveated, traceable output for allocative or strategic reasoning.

### 5. Archival clarity

Preserving interpretable summaries of runs or periods of work for later reinspection.

### 6. Communication

Translating technical and methodological structure into a more readable form without severing traceability.

These purposes are legitimate, but they should remain explicit.

---

## Report scope must remain bounded

A report should always answer a concrete question or bounded set of questions.

Examples:

- What allocation-relevant consequences emerge under this scenario?
- How did the baseline and perturbed runs differ?
- Which hypothesis set appears strongest under the current snapshot?
- What changed between two modeled world states?
- How robust is the reportable conclusion under altered assumptions?

A report should not drift into:

- general world explanation
- total commentary
- free-floating macro narrative
- rhetorical future-writing detached from artifact support

A report without a bounded question is structurally weak.

---

## Report identity

Reports are canonical artifacts and should follow the repository's identity logic.

Recommended ID format:

- `RPT-YYYYMMDD-###`

Examples:

- `RPT-20260312-001`
- `RPT-20260312-002`

Reports may also support versioning where meaningful, for example:

- `RPT-20260312-001@v2`

This is useful when a report is materially revised while remaining the same underlying report object.

See also `docs/ids-and-versioning.md`.

---

## Recommended report location

**Recommended directory:** `reports/`

Possible future structure:

- `reports/RPT-20260312-001.md`
- `reports/RPT-20260312-002.md`

or, if reports become bundles:

- `reports/RPT-20260312-001/report.md`
- `reports/RPT-20260312-001/appendix.yaml`
- `reports/RPT-20260312-001/traceability.yaml`

The exact format can evolve.

What matters is that reports remain canonical governed artifacts.

---

## Report types

The repository may eventually support multiple report types.

Useful categories may include:

- executive summary
- technical report
- scenario comparison report
- run summary report
- validation summary report
- historical replay report
- allocation implications report
- internal review memo

Not every report type needs identical structure.

But every report type should remain tied to explicit upstream artifacts.

---

## Recommended minimum fields

Every report should ideally support at least:

- `artifact_id`
- `artifact_type`
- `title`
- `status`
- `version` where applicable
- `created_at`
- `created_by` where relevant
- `report_type`
- `report_purpose`
- `problem_context`
- `scope`
- `snapshot_refs`
- `world_snapshot_refs`
- `hypothesis_refs`
- `scenario_refs`
- `run_refs`
- `result_refs`
- `validation_refs`
- `key_findings`
- `assumptions_in_force`
- `uncertainty_notes`
- `limitation_notes`
- `traceability_notes`
- `recommendation_notes` where appropriate
- `tags` where useful

The final implementation format can be decided later.

---

## Meaning of key report fields

### artifact_id

Stable report identity.

Example:
- `RPT-20260312-001`

### artifact_type

Should identify the artifact family clearly.

Example:
- `report`

### title

Human-readable report title.

### status

Current lifecycle state of the report.

Examples:
- `draft`
- `in_review`
- `published`
- `revised`
- `archived`
- `invalidated`

### report_type

The kind of report.

Examples:
- executive_summary
- technical_report
- run_summary
- scenario_comparison

### report_purpose

Why this report exists.

Examples:
- internal review
- comparison
- archival summary
- decision support
- publication support

### problem_context

The bounded problem space this report addresses.

### scope

What the report covers and does not cover.

### snapshot_refs / world_snapshot_refs

References to upstream input-state artifacts where relevant.

### hypothesis_refs

References to the hypotheses materially involved.

### scenario_refs

References to the scenarios materially involved.

### run_refs / result_refs

References to the executions and outputs interpreted by the report.

### validation_refs

References to the validation and evaluation artifacts that support the report's standing.

### key_findings

The main bounded takeaways.

### assumptions_in_force

The assumptions under which the findings are meaningful.

### uncertainty_notes

What remains uncertain and how that uncertainty matters.

### limitation_notes

What the report does not establish, cover, or justify.

### traceability_notes

How a reviewer can trace the report back through the artifact chain.

### recommendation_notes

Optional. Only where the report is intended to support bounded action or prioritization.

---

## Minimum report rule

A report should make it possible to answer all of the following:

- What question does this report address?
- What artifact chain does it depend on?
- Which assumptions are in force?
- Which results are being interpreted?
- What is actually being claimed?
- What is not being claimed?
- What uncertainties remain?
- What validation or evaluation supports the report?
- Can a reviewer trace the report back to the underlying artifacts?

If these questions cannot be answered, the report is under-governed.

---

## Report status model

Reports should support an explicit lifecycle state.

Recommended statuses:

- `draft`
- `in_review`
- `published`
- `revised`
- `archived`
- `invalidated`

### draft

The report exists but is not ready for active downstream use.

### in_review

The report is under active review and should not yet be treated as settled.

### published

The report is currently the active communicative form for its purpose.

### revised

The report has been materially updated while retaining its report identity.

### archived

The report is retained for history and comparison but is not current.

### invalidated

The report's standing has broken materially, for example because upstream artifacts were invalidated or the report overstepped what the evidence supported.

---

## Report and artifact-chain dependency

A report is only as strong as the artifact chain it depends on.

This means a report should not be interpreted independently from:

- the input state
- the world-state representation
- the hypotheses
- the scenarios
- the models
- the run manifests
- the results
- the validation records

A report may be easier to read than those artifacts.

It is not allowed to float free of them.

---

## Report and result distinction

A result is not yet a report.

### Result

Captures what came out of a run.

### Report

Interprets what that result means, under explicit assumptions and limitations.

This distinction matters because many overstatements happen at the transition from result to report.

A strong report should preserve that line clearly.

---

## Report and source distinction

A report is not a source substitute.

Even if a report summarizes source-derived conclusions well, it should not replace the underlying provenance chain.

This means:

- reports may summarize
- reports may synthesize
- reports may compare
- reports may interpret

But reports should not behave as if they themselves were the primary evidence layer.

---

## Report and recommendation distinction

Some reports may include recommendation-like implications.  
Others should not.

This distinction should remain explicit.

### Permissible recommendation logic

A report may include bounded recommendation notes when:

- the recommendation is clearly tied to the report's scope
- the assumptions are visible
- uncertainty is visible
- the recommendation is not overstated beyond the supporting artifact chain

### Impermissible recommendation logic

A report should not present:

- decontextualized prescriptions
- hidden normative leaps
- strong allocation claims unsupported by the upstream artifacts
- decision certainty where only exploratory output exists

A report is allowed to support decisions.  
It is not allowed to impersonate certainty.

---

## Report sections

A strong report will often contain some version of the following sections.

### 1. Question or objective

What the report is trying to answer.

### 2. Scope

What is included and excluded.

### 3. Upstream artifact basis

Which snapshots, hypotheses, scenarios, runs, and results are in force.

### 4. Method or artifact-chain summary

How the repository arrived at the outputs being discussed.

### 5. Key findings

What the report currently supports.

### 6. Assumptions in force

What had to hold for the findings to make sense.

### 7. Uncertainty and limitations

What remains unresolved or fragile.

### 8. Validation and evaluation status

What checking has been done.

### 9. Interpretation or implications

What these findings appear to mean within the report's bounded scope.

### 10. Traceability references or appendix

How to inspect the underlying chain.

Not every report must have exactly these headings, but the underlying functions should remain present.

---

## Key findings must remain bounded

A report should distinguish clearly between:

- observed outputs
- interpreted implications
- tentative judgments
- stronger conclusions

Useful framing patterns may include:

- the run indicates
- under the current assumptions
- the artifact chain supports
- the result appears sensitive to
- this should be treated as exploratory
- this conclusion is strong only if

Weak framing tends to erase these distinctions.

---

## Assumptions must remain visible

Reports often become misleading not because the underlying work was bad, but because assumptions disappear.

A strong report should preserve assumptions such as:

- time horizon
- scenario assumptions
- model simplifications
- input constraints
- missing actors
- boundary conditions
- parameter dependencies

Assumptions should not be hidden merely because they complicate the narrative.

---

## Uncertainty must remain explicit

A report should not present clarity where only bounded partial visibility exists.

Relevant uncertainties may include:

- uncertain inputs
- competing hypotheses
- scenario ambiguity
- model sensitivity
- incomplete validation
- interpretive ambiguity
- changing world conditions

Uncertainty is not a flaw to be concealed.  
It is part of the artifact's real status.

---

## Limitation notes are mandatory in spirit

Every meaningful report should make visible what it does not establish.

Examples:

- does not establish real-world causal certainty
- does not justify a universal claim
- does not generalize beyond the specified scenario set
- does not replace primary source review
- does not settle between rival explanations fully
- does not support strong decision confidence without further validation

A report without limitation notes tends to overstate itself.

---

## Traceability requirement

A reviewer should be able to move from the report back to the underlying artifacts.

This does not require the report body to become unreadable.

But it does require explicit references, appendix logic, or linked metadata.

A report should not leave the reviewer wondering:

- Which run is this about?
- Which scenario did this conclusion come from?
- Which hypothesis set was active?
- Was this based on a stale snapshot?
- Was the underlying result validated?

Traceability is not optional.

---

## Report and validation

A report should not claim more validation than actually exists.

Examples of bad practice:

- implying robustness that was never tested
- speaking as if a draft hypothesis were validated
- omitting that the run was exploratory
- hiding that the result was partial or anomalous
- presenting caveated internal output as if publication-ready

Reports should explicitly refer to the validation and evaluation layer where it matters.

See also `docs/validation-and-evaluation.md`.

---

## Report and interpretive honesty

Interpretive honesty is one of the most important report qualities.

A report is interpretively honest when it does not:

- smuggle in unsupported claims
- blur observed output and favored narrative
- downgrade uncertainty rhetorically
- hide dependence on fragile assumptions
- overstate actionability
- selectively present only confirming material

This matters especially in reports intended to support allocation or strategic reasoning.

---

## Report audiences

Reports may be written for different audiences, such as:

- repository maintainers
- internal reviewers
- technically informed collaborators
- decision-oriented readers
- future archival readers

Different audiences justify different styles and compression levels.

But no audience justifies severing the report from its artifact chain.

Audience adaptation is allowed.  
Epistemic laundering is not.

---

## Internal vs external reports

The repository may later distinguish between internal and external reports.

### Internal reports

May be more exploratory, technical, or rough, provided their provisional status remains explicit.

### External or publication-facing reports

Require stronger discipline in:
- traceability
- caveating
- validation visibility
- controlled language
- review status

The difference should remain visible.

---

## Comparative reports

A comparative report may examine:

- multiple scenarios
- multiple hypothesis sets
- multiple models
- multiple runs
- multiple time periods

Such reports are legitimate, but they require especially clear structure.

A comparative report should make explicit:

- what is being compared
- on what basis
- under what assumptions
- whether the compared objects are actually commensurable
- what the comparison does and does not show

Comparison without comparability logic is structurally weak.

---

## Executive summaries

Executive summaries may be useful, but they are high-risk artifacts.

They compress the most.

Therefore they should be especially careful to preserve:

- bounded scope
- key assumptions
- major uncertainty
- report status
- traceability path to fuller artifacts

An executive summary is not a license to overstate.

---

## Technical reports

Technical reports may include more detail on:

- artifact chain
- methodology
- model logic
- validation and robustness
- result structure
- appendix material

These are often preferable when auditability and internal review are priorities.

They should still remain readable enough to support meaningful review.

---

## Mutability rules

### Before publication or active use

A draft report may still be revised substantially.

### After publication or distribution

A materially used report should not be silently rewritten in place in a way that changes its substantive meaning without version visibility.

Allowed small changes may include:
- typo fixes
- formatting cleanup
- corrected links
- metadata cleanup

Material changes should generally lead to:
- a revised version
- a status update
- explicit note of change

Silent rewriting weakens auditability.

---

## Invalidated reports

A report may need to be invalidated if:

- upstream artifacts were invalidated materially
- key provenance failed
- a report conclusion overstated what the chain supported
- the report depended on a broken run or scenario
- comparison logic was unsound
- a key assumption was later shown false in a way that breaks the report's standing

Invalidation should remain explicit.

A report does not remain strong merely because it was once written.

---

## Review questions for reports

Before a report is treated as strong enough for active use, the following questions should be answerable:

- What question does this report answer?
- Which artifact chain supports it?
- Are the key assumptions visible?
- Are uncertainty and limitations visible?
- Does the report distinguish result from interpretation?
- Does it overstate validation status?
- Can a reviewer trace its claims backward?
- Would a careful reader know what not to conclude from it?

If these questions cannot be answered, the report is too weak.

---

## Recommended report registry

Reports should eventually appear in a registry, for example:

- `registry/reports.yaml`

The registry should make visible:

- report ID
- status
- type
- canonical report ref
- linked run refs
- linked result refs
- linked validation refs
- publication or archival status

See also `docs/registries.md`.

---

## Recommended future structure

A possible future report layout could be:

- `reports/RPT-20260312-001/report.md`
- `reports/RPT-20260312-001/metadata.yaml`
- `reports/RPT-20260312-001/traceability.yaml`

or a lighter structure such as:

- `reports/RPT-20260312-001.md`

The implementation can stay simple initially.

The architectural requirement is only that reports become governed artifacts rather than loose narrative endpoints.

---

## Relationship to other canonical files

This file should be read together with:

- `docs/artifacts.md`
- `docs/ids-and-versioning.md`
- `docs/contracts.md`
- `docs/registries.md`
- `docs/snapshots.md`
- `docs/validation-and-evaluation.md`
- `docs/run-manifests.md`

Those files define the artifact, identity, contract, governance, snapshot, validation, and execution context within which reports operate.

This file specializes that logic for interpretive output artifacts.

---

## Consequences for repository design

This file implies structural additions such as:

- explicit report artifacts
- report IDs and statuses
- traceability references in reports
- distinction between run outputs and reports
- report review status
- possible report-type differentiation
- explicit limitation and uncertainty sections
- report registry entries

The repository does not need to implement all of this immediately.  
But it should be designed so that reports do not become the place where rigor disappears.

---

## What this file does not define

This file defines the conceptual role and governance of reports.

It does not yet define:

- final report templates
- exact metadata schemas
- rendering pipelines
- export formats
- publication workflows
- style guides
- automatic traceability appendix generation

Those should be specified separately if implementation requires them.

---

## Status of this file

This file is canonical for:

- what a report is
- what a report must remain tied to
- how reports handle uncertainty, assumptions, and limitations
- how reports differ from results and sources
- how reports support traceable interpretation rather than narrative drift

Any future reporting system in this repository should either:

- follow this report logic directly, or
- document explicitly why an equivalent mechanism is being used instead
