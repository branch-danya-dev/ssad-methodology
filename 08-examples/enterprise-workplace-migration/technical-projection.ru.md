# Technical Projection · enterprise migration

[English version](technical-projection.md)

## Системный вопрос

Может ли исправление системной модели через SSAD изменить проектирование API и relational data, или SSAD только перестраивает документацию?

## Проблема исходной projection

В прежней synthetic portfolio implementation существовали поля:

```text
workplaces.migration_status
migration_schedule.readiness_status
```

REST-модель также отдавала один `migrationStatus`, который смешивал planning, readiness, execution, exceptions и workplace environment meaning.

В итоге technical projection незаметно заново определяла домен уже после того, как analytical model была исправлена.

## Рассуждение по SSAD

Technical artifact является downstream от canonical knowledge.

```text
CANONICAL SYSTEM KNOWLEDGE
        ↓
TECHNICAL PROJECTION
        ↓
REST / OpenAPI / PostgreSQL / read models
```

Если transport или persistence model противоречит canonical owner, должна меняться projection.

## Исправление API

Новая synthetic API projection разделяет owner-specific concepts:

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

Несколько generic mutations исчезли.

Вместо:

```text
PATCH arbitrary migration status
```

операции выражают системный смысл, например:

```text
reschedule a plan
approve or reject postponement
record an attempt
resolve a blocker
perform operational validation
```

Schedule также больше не принимает `readinessStatus`, как будто Planning владеет этим решением.

## Исправление data model

PostgreSQL projection теперь разделяет хранимые факты по semantic owner:

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

Физически эти записи всё ещё могут находиться в одной базе данных.

> **Одна база данных не означает одного semantic owner.**

## Derived read model

Operational users часто нужна одна строка, содержащая:

```text
current environment
latest readiness
active schedule
latest attempt
open blockers
latest operational validation
```

Поэтому проект использует derived `workplace_operational_view`.

Это намеренно read model:

```text
multiple canonical owners
        ↓
joined operational view
        ↓
reporting / filtering / dashboard
```

Aggregation остаётся удобной, не превращаясь во второй source of truth.

## Урок implementation-aware analysis

Этот кейс показывает важное свойство SSAD:

> **Canonical ownership — не только вопрос документации. Он ограничивает то, как contracts, mutations и storage должны представлять системный смысл.**

Исправленная domain model изменила:

- API resource boundaries;
- command semantics;
- state representation;
- database tables;
- idempotency design migration attempts;
- operational reporting views.

То есть SSAD способна обнаруживать implementation design defects, когда технические артефакты случайно объединяют ответственности, которые системная модель держит раздельно.

## Каноническая проектная истина

Полная technical projection:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

Основная область:

- `technical-projection/`

## Какие главы SSAD демонстрирует кейс

- [`03-analysis/interfaces/`](../../03-analysis/interfaces/)
- [`03-analysis/data/`](../../03-analysis/data/)
- [`03-analysis/integrations/`](../../03-analysis/integrations/)
- [`04-knowledge-structure/canonical-ownership/`](../../04-knowledge-structure/canonical-ownership/)
- [`03-analysis/synthesis/`](../../03-analysis/synthesis/)

Вернуться: [`Enterprise Workplace Migration application`](README.ru.md)
