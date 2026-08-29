# 02 — BOUND

[Русская версия](02-bound.ru.md)

## Question

What system are we analyzing?

## System of Interest

For this example, the system of interest is:

> **The Sheet Export Plugin solution**, whose responsibility is to orchestrate export of selected host-document sheets into local PDF files and report the result.

The plugin itself is the primary internal runtime component.

The host application and filesystem are external runtime authorities that materially shape the solution and therefore receive explicit analytical perspectives.

## In Scope

```text
sheet-selection consumption
export orchestration
per-sheet result handling
manifest creation
output-path handling
interaction with host export capability
interaction with local filesystem
whole-export result presented by the plugin
```

## Out of Scope

```text
editing the CAD document
host application's internal rendering engine
OS filesystem implementation
user authentication
cloud synchronization
remote storage
document-management systems
network transport
```

## Boundary Model

```text
User
  │
  ▼
[ Sheet Export Plugin ]
  │          │
  │          └──────────────► Local Filesystem
  │
  └─────────────────────────► CAD Host Application
```

Authority:

```text
Plugin
→ owns orchestration and interpretation

Host Application
→ owns source document state and export capability

Filesystem
→ owns persistence of generated files
```

## Perspective Consequence

The boundary suggests:

```text
business/
plugin/
host-application/
filesystem/
system/
```

It does **not** justify:

```text
backend/
frontend/
database/
integrations/
```

A generic `integrations/` owner is intentionally absent in the baseline.

## Gate

The boundary is sufficiently clear to distinguish owners from consumers.

Next: [`03-own.md`](03-own.md)
