# Playbook Quick Reference

[Русская версия](quick-reference.ru.md)

## Which Playbook?

```text
START
  │
  ├─ Is this a new system or a new subsystem without an existing baseline?
  │      └─ YES → NEW SYSTEM
  │
  └─ NO
      │
      ├─ Does a real system already exist?
      │      └─ NO → NEW SYSTEM
      │
      └─ YES
          │
          ├─ Is current-state knowledge trustworthy enough to act as baseline?
          │      └─ NO → EXISTING SYSTEM
          │
          └─ YES → CHANGE
```

## New System

Use when:

- greenfield product or service;
- new plugin;
- new major subsystem;
- architecture is not yet stabilized;
- current-state reconstruction is not needed.

Primary risk:

> designing downstream detail before responsibility and ownership are clear.

Start with: [`new-system.md`](new-system.md)

## Existing System

Use when:

- the system already runs;
- documentation is missing, stale, fragmented, or contradictory;
- code and runtime behavior are more trustworthy than documentation;
- migration from legacy documentation is needed;
- current state must be separated from target state.

Primary risk:

> documenting the architecture you wish existed instead of the architecture that actually exists.

Start with: [`existing-system.md`](existing-system.md)

## Change

Use when:

- a stable or baseline system model already exists;
- a feature or rule changes;
- an integration is added or changed;
- a provider or technology is replaced;
- data ownership or system boundary may move;
- architecture changes.

Primary risk:

> treating a system change as a local implementation task.

Start with: [`change.md`](change.md)

## When Unsure

If you cannot answer whether the baseline is trustworthy:

> start with **Existing System** until evidence and ownership are stable enough.

A false assumption of stability is more dangerous than a short reconstruction pass.
