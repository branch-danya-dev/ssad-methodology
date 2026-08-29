# 06 · Change

[Русская версия](README.ru.md)

This section explains how to analyze changes to an existing system.

> **What will the change actually affect, which system claims may stop being true, and what must be revalidated?**

The core path is:

```text
CHANGE REQUEST
      ↓
INITIAL SCOPE
      ↓
CHANGE SURFACE
      ↓
COMPATIBILITY & RISK
      ↓
SELECTIVE REOPENING
      ↓
REVIEW / IMPLEMENTATION / VERIFICATION
      ↓
STABILIZATION
```

Topics:

- [`initial-scope/`](initial-scope/) — separate the desired behavior change from a proposed implementation;
- [`change-surface/`](change-surface/) — identify affected responsibilities, owners, contracts, flows, trust and failures;
- [`compatibility-risk/`](compatibility-risk/) — inspect backward compatibility, migrations, mixed versions, rollout and rollback;
- [`selective-reopening/`](selective-reopening/) — reopen only canonical claims that may no longer be true and stabilize them again through evidence.

`06-change` is not a replacement delivery lifecycle. It is a cross-cutting analysis mechanism used inside [`02-workflow/`](../02-workflow/).

It reuses the perspectives from [`03-analysis/`](../03-analysis/), canonical ownership from [`04-knowledge-structure/`](../04-knowledge-structure/) and validation mechanics from [`05-collaboration/`](../05-collaboration/).

A useful impact vocabulary is:

```text
DIRECT
INDIRECT
POTENTIAL
OUT OF SCOPE
```

`OUT OF SCOPE` means the area was checked and does not need to be reopened.

The key principle is:

> **A change does not reopen all documentation. It reopens only claims about the system that may have stopped being true.**

Next: [`07-practice/`](../07-practice/).
