# Technical Projection · enterprise migration

[Русская версия](technical-projection.ru.md)

## System question

Can correcting the system model through SSAD change the design of APIs and relational data, or does SSAD only reorganize documentation?

## Original projection problem

The earlier synthetic portfolio implementation contained fields such as:

```text
workplaces.migration_status
migration_schedule.readiness_status
```

The REST model also exposed one `migrationStatus` that mixed planning, readiness, execution, exceptions and workplace environment meaning.

This meant the technical projection was silently redefining the domain after the analytical model had already been corrected.

## SSAD reasoning

A technical artifact is downstream from canonical knowledge.

```text
CANONICAL SYSTEM KNOWLEDGE
        ↓
TECHNICAL PROJECTION
        ↓
REST / OpenAPI / PostgreSQL / read models
```

If a transport or persistence model contradicts the canonical owner, the projection should change.

## API correction

The revised synthetic API separates owner-specific concepts:

```text
Workplace
→ environment state

Readiness
→ readiness evaluations

Planning
→ migration schedules / rescheduling

Execution
→ migration attempts

Exceptions
→ blockers / recovery actions

Operational completion
→ explicit operational validation
```

Several generic mutations disappeared.

Instead of:

```text
PATCH arbitrary migration status
```

operations represent system meaning, for example:

```text
reschedule a plan
approve or reject postponement
record an attempt
resolve a blocker
perform operational validation
```

A schedule also no longer accepts `readinessStatus` as if Planning owned the decision.

## Data correction

The PostgreSQL projection now separates stored facts by semantic owner:

```text
workplaces.environment_state
→ Workplace

readiness_evaluations
→ Readiness

migration_schedules
→ Planning

migration_attempts
→ Execution

migration_blockers
→ Exceptions

operational_validations
→ completion verification
```

These records may still live in one physical database.

> **One database does not imply one semantic owner.**

## Derived read model

Operational users often need a single row containing:

```text
current environment
latest readiness
active schedule
latest attempt
open blockers
latest operational validation
```

The project therefore uses a derived `workplace_operational_view`.

That is intentionally a read model:

```text
multiple canonical owners
        ↓
joined operational view
        ↓
reporting / filtering / dashboard
```

The aggregation is useful without becoming a second source of truth.

## Implementation-aware analysis lesson

This case demonstrates an important SSAD property:

> **Canonical ownership is not only a documentation concern. It constrains how contracts, mutations and storage should represent system meaning.**

The corrected domain model changed:

- API resource boundaries;
- command semantics;
- state representation;
- database tables;
- idempotency design for migration attempts;
- operational reporting views.

So SSAD can reveal implementation design defects when technical artifacts accidentally merge responsibilities that the system model keeps separate.

## Canonical project truth

Full technical projection:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

Relevant area:

- `technical-projection/`

## SSAD chapters demonstrated

- [`03-analysis/interfaces/`](../../03-analysis/interfaces/)
- [`03-analysis/data/`](../../03-analysis/data/)
- [`03-analysis/integrations/`](../../03-analysis/integrations/)
- [`04-knowledge-structure/canonical-ownership/`](../../04-knowledge-structure/canonical-ownership/)
- [`03-analysis/synthesis/`](../../03-analysis/synthesis/)

Back to: [`Enterprise Workplace Migration application`](README.md)
