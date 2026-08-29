# Change — Upload PDFs to External DMS

[Русская версия](README.ru.md)

> **Status:** synthetic change exercise  
> **Starting point:** [`../../baseline/`](../../baseline/)

## Change Request

> After local export, allow the user to upload successfully generated PDFs to an external document-management system (DMS).

## Why This Is Not Just a Plugin Task

The baseline boundary is:

```text
Plugin
├── Host Application
└── Local Filesystem
```

The requested behavior adds:

```text
Plugin
└── External DMS
```

Therefore the system boundary changes.

The change must be analyzed before detailed API or SDK design.

## Change Workflow

1. [`change-surface.md`](change-surface.md) — identify affected owners.
2. [`impact-analysis.md`](impact-analysis.md) — define the required knowledge changes.
3. [`verification.md`](verification.md) — verify authority, failure behavior, and traceability.

## Resulting Structural Change

Before:

```text
business/
plugin/
host-application/
filesystem/
system/
```

After:

```text
business/
plugin/
host-application/
filesystem/
integrations/
  dms/
system/
```

The new `integrations/` perspective appears **because the architecture now justifies it**.

It was not created in advance as an empty methodology folder.
