# Change impact checklist

[Русская версия](README.ru.md)

Use this when an existing system is changing and you need to determine the real impact.

Check:
- desired behavior versus proposed implementation;
- must-not-change invariants;
- initial scope and affected owners;
- responsibilities, ownership, behavior, states, data, interfaces, integrations, flows, trust, failures and operations;
- compatibility, migration, mixed versions, rollout and rollback;
- which canonical claims may stop being true.

Classify impact as:

```text
DIRECT
INDIRECT
POTENTIAL
OUT OF SCOPE
```

Minimum output:

```text
Desired change
Must-not-change invariants
Initial scope
Change Surface
Affected owners
Compatibility risks
Reopened knowledge
Verification targets
```

Go deeper:
- [`06-change/initial-scope`](../../06-change/initial-scope/)
- [`06-change/change-surface`](../../06-change/change-surface/)
- [`06-change/compatibility-risk`](../../06-change/compatibility-risk/)
- [`06-change/selective-reopening`](../../06-change/selective-reopening/)
