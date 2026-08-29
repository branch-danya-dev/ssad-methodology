# System Synthesis

[Русская версия](README.ru.md)

## Purpose

This perspective owns knowledge that spans business behavior, plugin orchestration, host authority, and filesystem persistence.

## System Context

```text
           User
            │
            ▼
   [ Sheet Export Plugin ]
       │             │
       │             ▼
       │       Local Filesystem
       │
       ▼
CAD Host Application
```

## End-to-End Flow

```text
User selection
→ Plugin preparation
→ Host export per sheet
→ Filesystem persistence
→ Plugin result aggregation
→ Manifest persistence
→ Final user result
```

## System Invariants

`SI-01` — Source document content remains unchanged by the export job.

`SI-02` — Every selected sheet has exactly one recorded item in the final manifest when manifest creation succeeds.

`SI-03` — A successful PDF is not removed because a later sheet fails.

`SI-04` — `SUCCESS` requires every selected sheet to succeed.

`SI-05` — `FAILED` means no selected sheet succeeded.

`SI-06` — Export failure must not reduce the set of valid pre-existing output files.

## Authority Map

```text
Source document truth
→ Host Application

Export-job interpretation
→ Plugin

Physical output persistence
→ Filesystem

Required observable behavior
→ Business rules

Cross-owner invariants
→ System synthesis
```

## Baseline Boundary

There is no network or external document-management integration.

A later change that adds one must reopen the boundary model rather than silently adding an HTTP call to plugin documentation.

See [`../../changes/dms-upload/`](../../changes/dms-upload/).
