# Responsibility Structure · enterprise migration

[Русская версия](responsibility-structure.ru.md)

## System question

How do we structure knowledge when the analyzed system is not one application, but a migration programme spanning workplaces, support domains, infrastructure tooling and operational coordination?

## Original difficulty

A document-oriented view suggests categories such as:

```text
requirements
business rules
API
SQL
diagrams
```

But those categories do not answer the system question:

> **Who owns which part of migration meaning?**

The real case contains several different responsibilities that can change independently.

## SSAD reasoning

Start from the object being changed and the decisions made around it.

```text
WORKPLACE
What working environment exists?

READINESS
May normal migration safely proceed now?

PLANNING
When is migration intended to happen?

EXECUTION
What actually happened during an attempt?

EXCEPTIONS
What changes the normal path and how is recovery handled?

INTEGRATIONS
What evidence, commands and notifications cross external boundaries?

SYSTEM
Do these local models form one coherent migration outcome?
```

The resulting repository structure follows these responsibility areas:

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

This structure is deliberately different from Aveli's `business/backend/frontend/database/...` layout.

That difference is evidence that SSAD does not prescribe one universal folder tree.

## What became clearer

The responsibility split exposed several distinctions that were previously easy to blur:

```text
planned migration
!= actual attempt

technical attempt success
!= operational completion

readiness evidence
!= readiness authority

blocker record
!= ownership of the underlying technical problem

storage location
!= semantic ownership
```

It also gave each future change a smaller reopening surface.

For example, changing postponement behavior primarily reopens `planning/` and relevant integration boundaries. It does not automatically reopen workplace-state semantics or attempt history.

## Canonical project truth

Full responsibility model:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

Relevant areas:

- `system/`
- `workplace/`
- `readiness/`
- `planning/`
- `execution/`
- `exceptions/`
- `integrations/`

## SSAD chapters demonstrated

- [`03-analysis/boundaries/`](../../03-analysis/boundaries/)
- [`03-analysis/responsibilities/`](../../03-analysis/responsibilities/)
- [`03-analysis/ownership/`](../../03-analysis/ownership/)
- [`04-knowledge-structure/storage-hierarchy/`](../../04-knowledge-structure/storage-hierarchy/)
- [`04-knowledge-structure/progressive-depth/`](../../04-knowledge-structure/progressive-depth/)

Next: [`global-status-decomposition.md`](global-status-decomposition.md)
