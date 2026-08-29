# Enterprise Workplace Migration · real-world SSAD application

[Русская версия](README.ru.md)

This application shows how SSAD behaves on a system that is materially different from a conventional software product.

Full reconstructed case:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

The case is a sanitized reconstruction of a large-scale enterprise workplace migration from Microsoft Windows to Astra Linux in a banking environment.

It is not modeled as an operating-system installer.

The analytical object is the **controlled evolution of an employee workplace while preserving the capability to perform required business activity**.

## Why this case matters for SSAD

Aveli helped validate SSAD on a product-shaped system with frontend, backend, local data, billing, trust and integrations.

Enterprise Workplace Migration tests a very different shape:

- there is no single application boundary containing the system;
- evidence is distributed across multiple support and infrastructure domains;
- readiness is a cross-team decision rather than a property of one component;
- planning and actual execution have independent histories;
- failures create explicit operational recovery paths;
- the same workplace can simultaneously have different readiness, planning, execution and exception states;
- technical API/database artifacts are only synthetic projections of the reconstructed domain.

This makes the case useful for testing whether SSAD generalizes beyond the system shape that helped create it.

## What applying SSAD changed

The original portfolio repository was organized by artifact type:

```text
docs/
api/
sql/
diagrams/
```

After applying SSAD, active knowledge is organized by system responsibility:

```text
system/
workplace/
readiness/
planning/
execution/
exceptions/
integrations/
technical-projection/
```

The important result is not the folder rename. The analysis itself changed.

For example, the former global migration status:

```text
Scheduled
Ready
Postponed
Blocked
Migration In Progress
Manual Migration Required
Dual Boot
Migrated
```

was decomposed into independent responsibility-owned dimensions.

## Application structure

```text
1. Responsibility Structure
   ↓
why a migration programme needs different owners than a product system

2. Global Status Decomposition
   ↓
why one migration_status hid several independent state models

3. Evidence and Readiness
   ↓
why distributed evidence does not imply distributed system meaning

4. Technical Projection
   ↓
how the corrected domain model changed REST and relational design
```

Together they demonstrate:

```text
SYSTEM BOUNDARY
↓
RESPONSIBILITY MODEL
↓
OWNERSHIP
↓
INDEPENDENT STATES
↓
CROSS-BOUNDARY EVIDENCE
↓
TECHNICAL PROJECTION
↓
SYSTEM SYNTHESIS
```

## How to read this application

Each slice answers four questions:

```text
What was difficult in the original case?
What did SSAD force us to separate?
What changed in the resulting model?
Where does canonical project truth live?
```

The application intentionally does not reproduce the full enterprise repository.

> **SSAD explains the reasoning. The project repository remains the canonical owner of project-specific truth.**

Start: [`responsibility-structure.md`](responsibility-structure.md)
