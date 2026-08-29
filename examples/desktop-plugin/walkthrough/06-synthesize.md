# 06 — SYNTHESIZE

[Русская версия](06-synthesize.ru.md)

## Question

What knowledge belongs to the whole system rather than to one owner?

The main component perspectives are now sufficiently understood to synthesize the system view.

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
1. User selects sheets in the host document.
2. Plugin reads the current selection.
3. Plugin obtains source-document identity.
4. Plugin creates an export job.
5. For each selected sheet:
   a. derive target file name;
   b. request host PDF export;
   c. record SUCCESS or FAILED.
6. Plugin builds the manifest.
7. Filesystem persists the manifest.
8. Plugin derives whole-job result:
   SUCCESS / PARTIAL_SUCCESS / FAILED.
9. User receives the final result.
```

## System Invariants

`SI-01` — Source document content remains unchanged by the export job.

`SI-02` — Every selected sheet has exactly one recorded item in the final manifest.

`SI-03` — A successful PDF already produced for another sheet is not removed because a later sheet fails.

`SI-04` — Whole-job `SUCCESS` is possible only when every sheet item succeeded.

`SI-05` — Whole-job `FAILED` means no sheet export succeeded.

## Why These Belong to `system/`

No single perspective owns all participating facts:

```text
BR-02
+
plugin orchestration
+
host export
+
filesystem persistence
=
SI-03
```

The invariant is therefore synthesized at the nearest common system-level owner.

## Output

The system can now be understood end-to-end without duplicating component detail.

Next: [`07-verify.md`](07-verify.md)
