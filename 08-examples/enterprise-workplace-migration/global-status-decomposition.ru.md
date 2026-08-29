# Global Status Decomposition · enterprise migration

[English version](global-status-decomposition.md)

## Системный вопрос

Что скрывает одно поле status, когда оно пытается одновременно представить planning, readiness, execution, exceptions и workplace environment?

## Исходная модель

В прежней portfolio-модели использовался один общий migration lifecycle:

```text
Scheduled
Ready
Postponed
Blocked
Migration In Progress
Manual Migration Required
Dual Boot
Migrated
Fully Operational
```

Это кажется удобным, пока системе не нужно одновременно выразить несколько истинных фактов.

Например:

```text
Рабочее место всё ещё Windows Operational.
Текущее readiness decision = RED.
Активный plan = Postponed.
Открыт software blocker.
```

Один `migration_status` не способен представить эти факты без потери смысла.

## Рассуждение по SSAD

Нужно спросить, кто владеет каждым утверждением.

```text
Windows Operational
Dual-Boot Transition
Astra Installed — Pending Validation
Astra Operational
→ Workplace

GREEN / YELLOW / RED
→ Readiness

Active / Superseded / Completed plan
→ Planning

Attempt started / failed / succeeded
→ Execution

Open / resolving / resolved blocker
→ Exceptions
```

Одна огромная state machine превращается в несколько небольших state models с явным responsibility ownership.

## Итоговая модель

Рабочее место теперь можно представить как набор независимых фактов:

```text
Environment = Windows Operational
Readiness = RED
Planning = Postponed
Execution = Last attempt failed
Exception = Missing critical software
```

Никакой synthetic master state не требуется.

Dashboard всё ещё может объединять эти dimensions для удобства, но derived value не должен становиться canonical owner.

```text
CANONICAL DIMENSIONS
        ↓
DERIVED OPERATIONAL VIEW
        ↓
UI / reporting / filtering
```

## Почему это важно для change analysis

Независимые states улучшают reasoning об impact изменений.

Если обнаружилась новая software incompatibility:

```text
compatibility evidence changes
        ↓
Readiness reopens
        ↓
possibly Planning reopens
```

Workplace environment при этом автоматически не меняется.

Так же successful technical attempt меняет Execution evidence и может перевести environment в `Astra Installed — Pending Validation`, но сам по себе не доказывает `Astra Operational`.

## Каноническая проектная истина

Полные state semantics:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

Основные области:

- `workplace/states.md`
- `readiness/decision-model.md`
- `planning/scheduling-and-postponement.md`
- `execution/attempt-model.md`
- `exceptions/blockers-and-recovery.md`
- `system/data-ownership.md`

## Какие главы SSAD демонстрирует кейс

- [`03-analysis/ownership/`](../../03-analysis/ownership/)
- [`03-analysis/states/`](../../03-analysis/states/)
- [`03-analysis/synthesis/`](../../03-analysis/synthesis/)
- [`06-change/change-surface/`](../../06-change/change-surface/)
- [`06-change/selective-reopening/`](../../06-change/selective-reopening/)

Далее: [`evidence-readiness.ru.md`](evidence-readiness.ru.md)
