# 04 — MODEL

[Русская версия](04-model.ru.md)

## Question

What behavior, data, and contracts must now be made explicit?

Ownership is stable enough to model downstream detail.

## Business Behavior

`BR-01` — Export must not modify the source document.

`BR-02` — Every selected sheet is attempted independently.

`BR-03` — A failure of one sheet must not delete already successful PDF outputs.

`BR-04` — The user receives a final result after all selected sheets have been processed.

## Plugin State Model

```text
Idle
  ↓
Preparing
  ↓
Exporting
  ↓
WritingManifest
  ↓
Completed
```

A sheet-level failure does not move the whole job directly to terminal failure.

Job result:

```text
SUCCESS
PARTIAL_SUCCESS
FAILED
```

## Host Contract

Conceptually:

```text
getSelectedSheets()
getDocumentIdentity()
exportSheetToPdf(sheetId, targetPath)
```

The exact API is intentionally not specified.

## Filesystem Contract

Conceptually:

```text
ensureOutputDirectory(path)
writeFile(path, bytes)
writeManifest(path, json)
```

Again, this describes responsibility, not an actual OS API.

## Manifest Model

```json
{
  "sourceDocumentId": "DOC-42",
  "exportedAt": "2030-01-01T10:00:00Z",
  "outputDirectory": "/exports/project-a",
  "items": [
    {
      "sheetId": "A101",
      "sheetName": "Floor Plan",
      "fileName": "A101-Floor-Plan.pdf",
      "status": "SUCCESS"
    }
  ]
}
```

The JSON is illustrative.

## Remaining Open Questions

`OPEN-01` file collision policy remains unresolved.

`OPEN-02` and `OPEN-03` are implementation-specific and do not block the conceptual baseline.

## Output

Behavior and interfaces are now detailed **after ownership**, not before it.

Next: [`05-connect.md`](05-connect.md)
