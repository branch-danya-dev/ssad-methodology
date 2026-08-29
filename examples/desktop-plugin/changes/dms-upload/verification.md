# Verification — DMS Upload Change

[Русская версия](verification.ru.md)

## Verification Questions

### Does DMS failure destroy local success?

Expected: **NO**

`BR-07` and the filesystem baseline require local output to remain valid.

### Does the DMS become authoritative for local export success?

Expected: **NO**

The DMS is authoritative only for remote document state.

### Can the plugin claim `UPLOADED` after an ambiguous timeout?

Expected: **NO**

An ambiguous timeout requires reconciliation against the DMS contract.

### Can a failed local export be uploaded?

Expected: **NO**

`BR-06` forbids it.

### Does the host application need to change?

Expected: **NO**

The DMS change is downstream of a successful local export.

## New Cross-System Invariants

`SI-07` — Remote upload failure never deletes or invalidates a locally successful PDF.

`SI-08` — `UPLOADED` may be recorded only after confirmed remote success or successful reconciliation.

`SI-09` — An item with local export failure cannot enter upload execution.

`SI-10` — Remote document identity is authoritative only within the DMS boundary.

## Traceability

```text
BR-07
    ↓
plugin upload state
    ↓
filesystem local retention
    ↓
integrations/dms failure behavior
    ↓
SI-07
    ↓
acceptance: local PDF remains after upload failure
```

## Result

The change can move toward a new stable baseline once:

- exact DMS contract is selected;
- authentication mechanism is defined;
- idempotency/reconciliation behavior is verified against that provider;
- affected baseline documents are updated.

The synthetic example intentionally stops before inventing provider-specific facts.

## Methodology Lesson

The Change Surface prevented the requirement from being reduced to:

```text
"add an API call"
```

Instead, it exposed authority, state, failure, trust, traceability, and a new analytical perspective.
