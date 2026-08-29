# Aveli — Methodology Findings

[Русская версия](methodology-findings.ru.md)

## 1. Folder Templates Are Too Rigid

Different systems need different physical owners.

> Analytical perspectives are required; folder templates are not.

## 2. Data Ownership Must Precede Persistence Detail

```text
ownership → conceptual → logical → physical
```

## 3. Technology Ownership Follows Responsibility

Initial mistake: Drift and Prisma were grouped with storage-engine documentation.

Correction:

```text
SQLite / PostgreSQL → database
Drift               → frontend
Prisma              → backend
RevenueCat boundary → integrations
```

## 4. Internal API Is Not an External Integration

```text
Aveli Frontend ↔ Aveli Backend
→ internal interface

Aveli ↔ RevenueCat / Stores / OS
→ external integration
```

## 5. System View Works Better as Late Synthesis

Early sketches are useful, but final system knowledge should be synthesized from stable component evidence.

## 6. Legacy Refactoring Needs Orphan-Knowledge Protection

```text
new owner
→ orphan check
→ migrate unique knowledge
→ fix references
→ remove duplicate legacy content
→ consistency review
```

## 7. Stable Does Not Mean No Future Questions

A stable baseline may contain classified future decisions, external evidence requirements, and architecture-change triggers.

## 8. SSAD Needs Workflow, Not Only Structure

Aveli revealed a repeatable pattern:

```text
discover → bound → own → model → connect → synthesize → verify → stabilize
```

This expanded SSAD from a documentation-organization model into a knowledge-lifecycle model.
