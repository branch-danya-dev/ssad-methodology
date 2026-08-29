# SSAD — System-Structured Analysis Documentation

> **Version:** v0.1 — Foundation  
> **Status:** Evolving methodology  
> **First full validation case:** Aveli

[Русская версия](README.ru.md)

## What SSAD Is

**System-Structured Analysis Documentation (SSAD)** is an approach to building, organizing, verifying, and evolving system-analysis knowledge around the real structure, responsibilities, boundaries, and dependencies of a system.

> **Documentation should mirror the system being analyzed.**

Traditional documentation often grows by artifact type:

```text
requirements/
diagrams/
api/
security/
database/
```

Real systems do not have that structure. One change may affect business rules, data, backend, frontend, security, integrations, acceptance, and verification at the same time.

SSAD therefore treats documentation as a **system knowledge model**, not as a folder of unrelated analyst deliverables.

## The Three SSAD Models

```text
WHERE does knowledge belong?
        ↓
Knowledge Architecture

HOW is knowledge discovered and stabilized?
        ↓
Analysis Workflow

HOW does knowledge change with the system?
        ↓
Change Model
```

### Knowledge Architecture

Defines canonical ownership, analytical perspectives, cross-references, progressive depth, technology ownership, and system-level synthesis.

### Analysis Workflow

```text
DISCOVER
   ↓
BOUND
   ↓
OWN
   ↓
MODEL
   ↓
CONNECT
   ↓
SYNTHESIZE
   ↓
VERIFY
   ↓
STABILIZE
   ↓
EVOLVE
```

These stages express **knowledge dependencies, not bureaucracy**.

### Change Model

```text
Change Request
      ↓
Change Surface
      ↓
Affected Owners
      ↓
Boundary / Data / Interface Impact
      ↓
Component / Technology / Trust Impact
      ↓
Acceptance + Traceability
      ↓
Verification
      ↓
Stable
```

The central concept is the **Change Surface**: the set of system knowledge owners affected by a change.

## Core Principles

1. **Documentation mirrors the system.**
2. **Ownership comes before detail.**
3. **Perspectives are required; folder templates are not.**
4. **Canonical knowledge has one owner.**
5. **Duplicate context when useful, not canonical truth.**
6. **Storage is hierarchical; knowledge is graph-based.**
7. **Data progresses from ownership to persistence.**
8. **Technology is an analytical object.**
9. **Evidence beats architectural preference.**
10. **System documentation is a synthesis layer.**
11. **Workflow stages represent dependency, not bureaucracy.**
12. **Changes are analyzed through their Change Surface.**

Detailed rationale: [`specification/core-principles.md`](specification/core-principles.md)

## Repository Structure

```text
ssad-methodology/
├── README.md
├── README.ru.md
├── specification/
├── workflow/
├── cases/
│   └── 001-aveli/
├── decisions/
├── proposals/
├── templates/
├── playbooks/
├── assets/
└── CHANGELOG.md
```

This is the structure of the **methodology repository**, not a mandatory SSAD project template.

## Recommended Reading Path

```text
README
  ↓
specification/methodology.md
  ↓
specification/core-principles.md
  ↓
workflow/construction.md
  ↓
workflow/change-analysis.md
  ↓
workflow/verification.md
  ↓
cases/001-aveli/
```

## First Validation Case — Aveli

The first full validation case is **Aveli**, a local-first mobile workspace. It forced the methodology to address product rules, local/server data ownership, frontend/backend responsibility, internal vs external boundaries, technology ownership, offline behavior, traceability, system synthesis, legacy-documentation migration, and final consistency review.

Case summary: [`cases/001-aveli/`](cases/001-aveli/)

Full project: https://github.com/branch-danya-dev/aveli-system-analysis

## What SSAD Does Not Replace

SSAD does not replace UML, BPMN, C4, ADRs, OpenAPI, database schemas, source code, tests, product management, operational runbooks, or architecture governance.

SSAD defines **how these forms of knowledge can be owned, connected, constructed, reviewed, and evolved around the system itself**.

## Current Scope of v0.1

`v0.1` focuses on:

```text
methodology definition
knowledge architecture
analysis workflow
change workflow
evidence model
maturity model
roles and stewardship
verification
maintenance
first validation case
```

Templates, practical playbooks, machine-readable metadata, automation, and additional validation cases are intentionally deferred.

## Working Definition

> **System-Structured Analysis Documentation is an evolving approach to building, organizing, verifying, and evolving system-analysis knowledge around the actual structure, responsibilities, boundaries, and dependencies of a system.**

Current maturity:

```text
SSAD v0.1
Foundation
First full validation case: Aveli
```
