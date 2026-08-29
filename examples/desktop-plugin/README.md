# Worked Example — Desktop Plugin

[Русская версия](README.ru.md)

> **Status:** synthetic worked example  
> **Purpose:** show the full relationship between SSAD workflow, stable knowledge ownership, and change analysis.

## Scenario

A fictional desktop CAD plugin exports selected drawing sheets to PDF.

Baseline behavior:

- the plugin runs inside a host CAD application;
- the user selects sheets in the host document;
- the plugin asks the host application to export each selected sheet to PDF;
- generated files are written to a user-selected local folder;
- the plugin writes `export-manifest.json` with the export result;
- the plugin does not modify the source document;
- one failed sheet does not cancel successful exports of other sheets;
- there is no backend, cloud database, or network dependency.

The initial stable system shape is therefore:

```text
business/
plugin/
host-application/
filesystem/
system/
```

No `backend/`, `frontend/`, or `integrations/` area exists because the baseline system does not justify those owners.

## How to Read This Example

### 1. Walkthrough

[`walkthrough/`](walkthrough/)

Shows **how knowledge is constructed**:

```text
DISCOVER
→ BOUND
→ OWN
→ MODEL
→ CONNECT
→ SYNTHESIZE
→ VERIFY
→ STABILIZE
```

### 2. Baseline

[`baseline/`](baseline/)

Shows **where the resulting stable knowledge belongs**:

```text
business/
plugin/
host-application/
filesystem/
system/
```

This is the key SSAD distinction:

> Workflow order is not repository ownership structure.

### 3. Change

[`changes/dms-upload/`](changes/dms-upload/)

Adds a new request:

> Upload successfully generated PDFs to an external document-management system.

This introduces a new external boundary and demonstrates Change Surface analysis.

## What This Example Demonstrates

- evidence-first construction even in a synthetic exercise;
- system boundary before implementation detail;
- ownership before contracts;
- optional perspectives;
- system-shaped stable documentation;
- traceability across owners;
- late system synthesis;
- verification before Stable;
- a new `integrations/` perspective appearing only when a real change justifies it.

## Synthetic Nature

All product behavior, constraints, components, and technical details in this directory are fictional teaching assumptions.

They are internally consistent for the example but are not implementation evidence for a real product.
