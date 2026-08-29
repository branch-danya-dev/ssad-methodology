# 01 — DISCOVER

[Русская версия](01-discover.ru.md)

## Question

What do we actually know before designing the documentation?

Because this is a synthetic example, the following statements are **declared scenario evidence** rather than evidence from a real implementation.

They play the role that stakeholder statements, code, contracts, or runtime observations would play in a real application.

## Declared Evidence

`E-01` — The plugin runs inside a desktop CAD host application.

`E-02` — The user selects one or more drawing sheets in the currently open document.

`E-03` — The host application exposes a PDF export capability to the plugin.

`E-04` — The user chooses a local output directory.

`E-05` — The plugin creates one PDF per selected sheet.

`E-06` — The plugin writes `export-manifest.json` describing the export result.

`E-07` — Failure of one sheet does not remove already successful exports.

`E-08` — The source CAD document must not be modified by the export operation.

`E-09` — The baseline has no backend, remote API, cloud database, or account model.

## Initial Unknowns

```text
OPEN-01
What happens if the output file already exists?

OPEN-02
What exact host API represents sheet identity?

OPEN-03
Does the host export synchronously or asynchronously?

OPEN-04
What fields are required in export-manifest.json?
```

These questions are visible, but not all of them block the next step.

## Initial Vocabulary

```text
Source Document
Sheet
Export Job
Export Result
Output Directory
PDF File
Export Manifest
Host Application
Plugin
```

## Output of DISCOVER

We now have enough information to ask:

> What exactly is inside the analyzed system, and what remains external?

Next: [`02-bound.md`](02-bound.md)
