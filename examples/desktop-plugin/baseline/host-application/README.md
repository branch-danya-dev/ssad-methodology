# Host Application Perspective

[Русская версия](README.ru.md)

## Responsibility

The CAD host application is authoritative for:

```text
open source document
document identity
sheet identity
sheet name
current sheet selection
PDF export capability
```

The plugin may consume or temporarily copy these values, but it does not become their canonical owner.

## Conceptual Contract

The plugin needs capabilities equivalent to:

```text
getDocumentIdentity()
getSelectedSheets()
exportSheetToPdf(sheetId, targetPath)
```

Exact API names, signatures, sync/async behavior, and vendor-specific objects are intentionally outside this synthetic example.

## Mutation Boundary

The export workflow must not require mutation of the source document.

This supports [`BR-01`](../business/).

## Failure Semantics

The host may report export failure for an individual sheet.

The host does not decide the whole multi-sheet job result. That interpretation belongs to the plugin.

## Open Implementation Questions

```text
OPEN-02
Exact representation of sheet identity.

OPEN-03
Exact synchronous or asynchronous behavior of export.
```

These questions do not invalidate the conceptual baseline.
