# Change Surface — DMS Upload

[Русская версия](change-surface.ru.md)

## First Pass

| Perspective / Concern | Impact | Why |
|---|---|---|
| Business | YES | upload becomes user-visible behavior |
| System boundary | YES | external DMS is added |
| Plugin | YES | upload orchestration and local status appear |
| Host Application | NO | host export responsibility does not change |
| Filesystem | YES | manifest records upload state |
| Integrations | YES / NEW | cross-boundary DMS contract now exists |
| Data ownership | YES | local upload status and remote document state must be separated |
| Trust / security | YES | external authentication and remote authority appear |
| Failure / recovery | YES | local success can coexist with upload failure |
| Acceptance | YES | upload outcomes must be observable |
| Traceability | YES | new behavior must trace to new integration and status model |

## Boundary Questions

```text
Does a new external system appear?
→ YES

Does source-document ownership move?
→ NO

Does PDF persistence move to DMS?
→ NO
Local PDFs remain locally authoritative for local export output.

Does the DMS become authoritative for remote document existence?
→ YES
```

## Ownership Questions

New knowledge:

```text
Upload intent / local upload status
→ Plugin

Physical local PDF
→ Filesystem

Remote document identity / remote existence
→ DMS

Cross-boundary request, auth, retry and reconciliation semantics
→ integrations/dms/

Whole-system meaning of local-success + remote-failure
→ system/
```

## Key Finding

A naive implementation might say:

```text
Plugin
→ POST /documents
```

SSAD first exposes the deeper change:

```text
new authority
+
new failure mode
+
new trust boundary
+
new data state
+
new acceptance behavior
```

That is the real Change Surface.
