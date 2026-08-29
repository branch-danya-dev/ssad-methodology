# SSAD Methodology

[Русская версия](methodology.ru.md)

## Purpose

SSAD manages **system-analysis knowledge** as an engineered model of the system.

It combines:

```text
Knowledge Architecture
Analysis Workflow
Change Model
```

The repository tree is only a physical projection of these models.

## Knowledge Architecture

Knowledge Architecture determines analytical perspectives, canonical ownership, boundaries between knowledge owners, cross-references, progressive depth, technology ownership, and traceability.

The methodology requires analytical questions to be answerable. It does not require identical directory names.

## Analysis Workflow

Canonical stages:

```text
DISCOVER
BOUND
OWN
MODEL
CONNECT
SYNTHESIZE
VERIFY
STABILIZE
EVOLVE
```

A later stage may reopen an earlier stage. The sequence expresses dependency, not a one-pass lifecycle.

## Change Model

The key artifact is the **Change Surface**:

```text
Change
  ↓
Affected analytical perspectives
  ↓
Affected canonical owners
  ↓
Affected contracts / data / behavior / trust
```

The Change Surface is established before detailed implementation documentation is rewritten.

## Truth Model

When uncertainty matters:

```text
VERIFIED
INFERRED
OPEN
```

Target-state proposals remain separate from current-state truth.

## Maturity Model

```text
Draft
→ Baseline
→ Stable
```

`Stable` means sufficiently cross-checked against relevant evidence, contracts, implementation, or stakeholder decisions.

## Canonical Ownership

For important knowledge determine:

```text
Who decides?
Who stores canonical state?
Who may change it?
Who consumes it?
Who verifies it?
```

Ownership should be understood before dependent detail is stabilized.

## System Synthesis

System-level knowledge owns relationships no single component can own:

- end-to-end flows;
- trust and authority;
- cross-component data movement;
- system invariants;
- boundary-changing evolution;
- whole-system failure scenarios.

## Examples and Applications

SSAD distinguishes two forms of methodology evidence and explanation.

### Example

An **Example** is synthetic or intentionally simplified.

It MAY describe any plausible implementation needed to explain or explore the methodology.

An example:

- does not have to correspond to a real product;
- may be deliberately shaped to expose one analytical problem;
- is useful for teaching, comparison, and low-cost methodology exploration;
- MUST NOT be presented as evidence that the described implementation exists.

Examples live in [`../examples/`](../examples/).

### Application

An **Application** is a real project in which SSAD is actually used.

An application:

- has real project constraints and evidence;
- links to real system-analysis documentation;
- can reveal methodology defects that synthetic examples do not expose;
- is stronger evidence of practical applicability.

Applications live in [`../applications/`](../applications/).

Current real-world application: [`../applications/aveli/`](../applications/aveli/)

## Methodology Evolution

Preferred path:

```text
Observed problem
→ Example exploration and/or Application evidence
→ Proposed rule
→ Validation
→ Accepted methodology
```

Synthetic examples may explore consequences before a rule is accepted. Real applications should be used whenever available to validate that the rule survives actual project constraints.

Significant accepted decisions belong in `decisions/`; unresolved methodology ideas belong in `proposals/`.

## Operational Playbooks

Playbooks are a practical guidance layer built on top of the canonical workflow.

They do not define new system perspectives and do not prescribe repository structure.

They map common starting conditions to the parts of the SSAD workflow that deserve the most attention:

```text
new system
→ establish boundary and ownership before dependent design

existing system
→ reconstruct current truth from evidence before target-state work

change
→ identify Change Surface and reopen only affected knowledge
```

The current core playbooks are:

- [`../playbooks/new-system.md`](../playbooks/new-system.md)
- [`../playbooks/existing-system.md`](../playbooks/existing-system.md)
- [`../playbooks/change.md`](../playbooks/change.md)

> **Workflow is normative methodology structure. Playbooks are operational guidance for applying it.**
