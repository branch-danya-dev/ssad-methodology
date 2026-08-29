# Business Perspective

[Русская версия](README.ru.md)

## Purpose

Allow a user working in a desktop CAD document to export selected drawing sheets to local PDF files without changing the source document.

## In Scope

- export of selected sheets;
- local output directory;
- one result per selected sheet;
- final export summary;
- export manifest;
- safe behavior when output files already exist.

## Out of Scope

- editing the CAD document;
- cloud storage;
- user accounts;
- remote collaboration;
- document-management integration;
- network transport.

## Business Rules

`BR-01` — Export must not modify the source document.

`BR-02` — Every selected sheet is attempted independently.

`BR-03` — Failure of one sheet must not delete already successful outputs of other sheets.

`BR-04` — The user receives a final result after all selected sheets are processed.

`BR-05` — Existing output files must not be destructively overwritten without explicit user approval.

## Acceptance

The baseline is acceptable when:

- every selected sheet has a recorded result;
- successful PDFs remain available after another sheet fails;
- the source document is unchanged;
- existing output files are protected according to `BR-05`;
- the final result distinguishes success, partial success, and total failure.

## Technical Consequences

Implementation details are owned elsewhere:

- orchestration → [`../plugin/`](../plugin/)
- source-document/export authority → [`../host-application/`](../host-application/)
- file persistence → [`../filesystem/`](../filesystem/)
- cross-system invariants → [`../system/`](../system/)
