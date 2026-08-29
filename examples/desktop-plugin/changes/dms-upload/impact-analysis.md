# Impact Analysis — DMS Upload

[Русская версия](impact-analysis.ru.md)

## Business Delta

Add:

`BR-06` — Only locally successful PDFs are eligible for upload.

`BR-07` — Upload failure must not invalidate or delete a successful local export.

`BR-08` — The user must be able to distinguish local export status from remote upload status.

`BR-09` — A failed upload may be retried without requiring the sheet to be exported again when the local PDF is still valid.

## Plugin Delta

The plugin gains upload orchestration after local export.

Per item:

```text
exportStatus
uploadStatus
remoteDocumentId?
uploadErrorCode?
```

Suggested upload status model:

```text
NOT_REQUESTED
PENDING
UPLOADING
UPLOADED
UPLOAD_FAILED
```

The plugin owns local interpretation of these statuses.

It does not own the remote truth represented by `remoteDocumentId`.

## Filesystem Delta

The manifest now persists upload-related local state.

A valid local PDF must remain available even when:

```text
network unavailable
DMS authentication rejected
DMS request times out
DMS returns server error
```

## New Integration Owner

New canonical area:

```text
integrations/dms/
```

It should own:

- external DMS responsibility;
- authentication boundary;
- upload contract;
- remote identity mapping;
- idempotency expectations;
- retry rules;
- reconciliation after ambiguous timeout;
- provider-specific failure semantics.

It should **not** own the business meaning of "successful export".

## Data Ownership Delta

```text
Local PDF bytes
→ Filesystem

Local export status
→ Plugin

Local upload-attempt status
→ Plugin

Remote document record
→ DMS

Mapping local sheet/export item ↔ remoteDocumentId
→ Integration relationship, persisted locally as needed
```

## System Delta

New whole-system states are possible:

```text
LOCAL_SUCCESS + REMOTE_UPLOADED
LOCAL_SUCCESS + REMOTE_PENDING
LOCAL_SUCCESS + REMOTE_FAILED
LOCAL_FAILED  + REMOTE_NOT_REQUESTED
```

This means one combined `SUCCESS/FAILED` flag is no longer expressive enough for the evolved system.

## Structural Delta

Only now does the architecture justify:

```text
integrations/
└── dms/
```

This is a direct demonstration of:

> **Perspectives are required; folder templates are not.**
