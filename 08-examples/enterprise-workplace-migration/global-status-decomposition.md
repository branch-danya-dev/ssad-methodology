# Global Status Decomposition · enterprise migration

[Русская версия](global-status-decomposition.ru.md)

## System question

What does a single status field hide when it tries to represent planning, readiness, execution, exceptions and the workplace environment at once?

## Original model

The earlier portfolio model used one broad migration lifecycle:

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

That looks convenient until two facts need to be true at the same time.

For example:

```text
The workplace is still Windows Operational.
The current readiness decision is RED.
The active plan is Postponed.
A software blocker is open.
```

One `migration_status` cannot represent those facts without collapsing meaning.

## SSAD reasoning

Ask who owns each statement.

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

This turns one giant state machine into several smaller state models with explicit responsibility.

## Resulting model

A workplace can now be represented as a vector of independent facts:

```text
Environment = Windows Operational
Readiness = RED
Planning = Postponed
Execution = Last attempt failed
Exception = Missing critical software
```

No synthetic master state is required.

A derived dashboard may still flatten these dimensions for convenience, but that derived value must not become the canonical owner.

```text
CANONICAL DIMENSIONS
        ↓
DERIVED OPERATIONAL VIEW
        ↓
UI / reporting / filtering
```

## Why this matters for change analysis

Independent states also improve change impact reasoning.

If a new software incompatibility appears:

```text
compatibility evidence changes
        ↓
Readiness reopens
        ↓
possibly Planning reopens
```

The workplace environment does not automatically change.

Likewise, a successful technical attempt changes Execution evidence and may move the environment to `Astra Installed — Pending Validation`, but it does not automatically prove `Astra Operational`.

## Canonical project truth

Full state semantics:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

Relevant areas:

- `workplace/states.md`
- `readiness/decision-model.md`
- `planning/scheduling-and-postponement.md`
- `execution/attempt-model.md`
- `exceptions/blockers-and-recovery.md`
- `system/data-ownership.md`

## SSAD chapters demonstrated

- [`03-analysis/ownership/`](../../03-analysis/ownership/)
- [`03-analysis/states/`](../../03-analysis/states/)
- [`03-analysis/synthesis/`](../../03-analysis/synthesis/)
- [`06-change/change-surface/`](../../06-change/change-surface/)
- [`06-change/selective-reopening/`](../../06-change/selective-reopening/)

Next: [`evidence-readiness.md`](evidence-readiness.md)
