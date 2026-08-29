# Filesystem Perspective

[Русская версия](README.ru.md)

## Responsibility

The filesystem owns physical persistence of:

```text
generated PDF files
export-manifest.json
pre-existing output files
```

It does not own the semantic meaning of an export result.

## Persistence Rules

`FS-01` — Successful PDF output remains present unless an explicitly approved later operation replaces it.

`FS-02` — Failure of a later sheet must not remove another sheet's successful PDF.

`FS-03` — A pre-existing file must not be destructively overwritten without explicit approval.

`FS-04` — A failed replacement attempt must not destroy the pre-existing valid file.

## Collision Strategy

The conceptual baseline allows either:

```text
explicit overwrite approval
```

or:

```text
non-conflicting generated filename
```

The exact UI is not canonical here.

## Manifest Persistence

The plugin owns manifest content; the filesystem persists it.

If manifest writing fails after PDFs were created, the system must report a failure state without pretending the manifest exists.

That whole-system interpretation belongs to [`../system/`](../system/).

## Boundary

Filesystem technology details are intentionally unspecified. The example models persistence responsibility, not an operating-system implementation.
