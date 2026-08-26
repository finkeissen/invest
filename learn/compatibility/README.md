# Compatibility

This directory describes how the framework's concepts can interface
with established external systems — exam frameworks, spaced-repetition
tools, learning management systems.

What is here:
- the **structural form** an alignment file takes,
- the obligations a compliant alignment must satisfy,
- the boundary between framework concepts and external concepts.

What is **not** here:
- concrete curriculum mappings,
- detailed crosswalks against any specific exam framework,
- alignment data ready to operationalise.

These exist outside this repository.

---

## Why interface, not absorb

Exam frameworks, spaced-repetition tools, and LMSes have their own
authority structures, their own definitions, and their own update cadences.

The framework does not absorb them.
It declares how to talk to them, while preserving its own contracts.

A correct alignment:
- **maps** external categories to framework concepts where structure permits,
- **declares non-mapping** where it does not,
- does not silently flatten distinctions in either direction.

---

## Structural form of an alignment file

An alignment file is expected to contain:

1. The external system's identifier (name, version, jurisdiction where applicable).
2. A list of mappings, each containing:
   - an external category or item identifier,
   - a framework concept identifier (or a declared *non-mapping*),
   - the dimension shift level the external category presupposes,
   - structural notes where presupposition is uncertain.
3. A declaration of the date and version of the external system the
   alignment was constructed against.
4. An admissibility status under the framework's contracts.

Concrete alignment data is implementation detail and is not published here.

---

## Recognised interface targets (structural)

The following classes of external systems are recognised as legitimate
interface targets. Specific systems are not enumerated.

- **National or international exam frameworks** — interfaces declare
  exam-defined topics as external categories with associated
  dimension shift presuppositions.
- **Spaced-repetition tools** — interfaces declare which artifact
  types may be exported to which deck structures, and what is lost
  in the export.
- **Learning management systems** — interfaces declare which framework
  artifacts are surfaced through which LMS objects, and which are not
  surfaced at all.

What is **not** lost in the framework remains the framework's record.
What is **not** representable in the external system is declared as
such, not silently dropped.

---

## STOP across the boundary

An alignment may itself reach STOP if:
- the external system has changed in a way the alignment has not been
  updated to reflect,
- a mapping would require violating one of the framework's contracts,
- the external system's structure cannot be reconstructed in a form
  the framework's contracts can speak about.

A STOP'ed alignment does not silently degrade to "best effort".
It is recorded, and the affected interactions are blocked at the boundary.
