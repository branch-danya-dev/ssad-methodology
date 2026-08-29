# Plugin Perspective

[Русская версия](README.ru.md)

## Responsibility

The plugin owns **export-job orchestration and interpretation**.

It does not own source-document truth or physical file persistence.

## Inputs

From the host application:

```text
source document identity
selected sheet identities
sheet names
per-sheet export outcome
```

From the user:

```text
output directory
overwrite approval when required
```

## Job State

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

A sheet failure is recorded locally to the job and does not immediately terminate processing of remaining sheets.

## Whole-Job Result

```text
SUCCESS
→ all selected sheets succeeded

PARTIAL_SUCCESS
→ at least one succeeded and at least one failed

FAILED
→ no selected sheet succeeded
```

## Manifest Semantic Ownership

The plugin owns the meaning and content of:

```text
sourceDocumentId
exportedAt
outputDirectory
items[]
  sheetId
  sheetName
  fileName
  status
  errorCode?
```

The filesystem only persists the resulting bytes.

## Boundary

The plugin consumes the host boundary documented in [`../host-application/`](../host-application/) and persistence behavior documented in [`../filesystem/`](../filesystem/).

Cross-component behavior belongs to [`../system/`](../system/).
