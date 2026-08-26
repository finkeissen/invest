# Contract: Agent Roles

**Status:** Normative · **Version:** 1.0

---

## Scope

This contract defines the **roles** an implementation may declare
when assigning behaviour to agents (human or automated).

It defines **obligations and prohibitions per role**.
It does not define:
- prompts, templates, or model bindings,
- routing logic between roles,
- which agent types or models implement which role,
- conversational style.

The repository is silent on operational implementation by design.

---

## Recognised roles

Four roles are recognised structurally.
Implementations may use different names, but the obligations attach
to whichever entity performs the role.

### 1. Tutor role

**Obligation:**
Engages the learner in interactions that produce observable evidence
relevant to gaps, interventions, and dimension shift levels.

**Required behaviour:**
- Records evidence in a form consumable by the framework's contracts.
- Names errors when they occur, rather than confirming them.
- Refuses to assert a dimension shift level the interaction has not
  established.

**Prohibited:**
- Confirming an incorrect response to maintain rapport.
- Inferring a level above what the response content establishes.
- Producing content presented as factual when the agent cannot
  verify it.

### 2. Routing role

**Obligation:**
Selects, for a given task, an agent or resource capable of fulfilling it.

**Required behaviour:**
- Records the basis of the selection in a form the framework can audit.
- Declines to route tasks for which no admissible agent exists.

**Prohibited:**
- Routing tasks to agents declared incapable of them.
- Silently substituting one agent for another after a routing decision.

### 3. Audit role

**Obligation:**
Checks that artifacts produced by other roles satisfy the relevant contracts.

**Required behaviour:**
- Marks artifacts STOP that violate their contracts.
- Records the violated obligation, not only the violation.

**Prohibited:**
- Editing artifacts to make them admissible after the fact.
- Approving artifacts whose admissibility cannot be established.

### 4. Recovery role

**Obligation:**
Engages with a learner when interaction has become structurally
unproductive (repeated STOP, sustained absence of progress, signs
of overload).

**Required behaviour:**
- Suspends or modifies interventions, with a recorded reason.
- Restores admissibility before further interventions are declared.

**Prohibited:**
- Continuing interventions while the recovery condition persists.
- Treating recovery as a learning intervention.

---

## Composition

A single agent (human or automated) may perform multiple roles,
**provided** the roles' obligations remain individually satisfiable
and their prohibitions are not in tension.

Where a tension exists (for example, between Tutor and Audit on the
same artifact), the roles MUST be separated across distinct agents.

---

## Operational realisation

How these roles are implemented — which prompts, which models, which
orchestration, which conversational design — is **out of scope**.

This contract specifies only:
- what each role must do,
- what each role must not do,
- how role obligations interact.

Implementations may publish their own role specifications.
This repository does not.
