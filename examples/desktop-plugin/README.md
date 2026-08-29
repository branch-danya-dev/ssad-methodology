# Example — Desktop Plugin

[Русская версия](README.ru.md)

> **Status:** synthetic example  
> **Purpose:** demonstrate a system shape where `backend/` and `frontend/` are not useful top-level owners.

## Scenario

A fictional CAD plugin exports selected drawing sheets to PDF and writes an export manifest next to the generated files.

The plugin runs entirely inside a desktop host application.

Assumptions:

```text
Plugin
Host CAD application
Local filesystem
OS print/PDF service
No backend
No cloud database
```

## Possible SSAD Perspectives

```text
business/
plugin/
host-application/
filesystem/
integrations/
system/
```

This is the important point: SSAD does not force:

```text
backend/
frontend/
database/
```

when those perspectives do not describe the real system.

## Ownership Example

```text
Export command orchestration
→ plugin

Open document / selected sheets
→ host application

Generated PDF files
→ filesystem

Print capability
→ OS service

Export result interpretation
→ plugin
```

## Boundary Example

The host application is not merely "a library". It owns document state and exposes the runtime environment in which the plugin operates.

That can justify an explicit `host-application/` perspective.

## Change Surface Example

Change request:

> Add automatic upload of generated PDFs to a document-management service.

Before the change:

```text
Plugin → Host → Filesystem
```

After the change:

```text
Plugin → Host
Plugin → Filesystem
Plugin → External DMS
```

The external system boundary changes, so an `integrations/` owner becomes more significant.

## Intentionally Simplified

The example does not prescribe a CAD vendor, plugin API, programming language, PDF engine, or DMS provider.
