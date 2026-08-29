# Changelog

## v0.2.0 — Worked Example

Introduced the first full synthetic SSAD walkthrough.

### Added

- `examples/desktop-plugin/walkthrough/` showing:
  - DISCOVER;
  - BOUND;
  - OWN;
  - MODEL;
  - CONNECT;
  - SYNTHESIZE;
  - VERIFY;
  - STABILIZE;
- `examples/desktop-plugin/baseline/` showing the stable system-shaped result of that workflow;
- explicit separation between temporal analysis order and canonical knowledge ownership;
- a verification loop that reopens an upstream business/filesystem rule;
- `examples/desktop-plugin/changes/dms-upload/` as the first worked Change Surface exercise;
- a structural example where `integrations/` appears only after a change actually creates an external integration.

### Changed

- Desktop Plugin promoted from a focused example to the first **worked example**;
- root README now links directly to walkthrough, baseline, and change-analysis views;
- `examples/README.*` now distinguishes focused and worked examples;
- current maturity updated to `v0.2.0`.

### Methodology Demonstrated

The worked example makes this distinction explicit:

```text
workflow/
→ how knowledge is constructed

system-shaped baseline/
→ who owns stable knowledge

change analysis/
→ how stable knowledge evolves
```


---

## v0.1.2 — Examples and Applications

Separated synthetic methodology examples from real-world applications.

### Added

- `examples/` for fictional or intentionally simplified systems;
- `applications/` for real projects actually documented using SSAD;
- mobile-application, desktop-plugin, and event-driven-platform synthetic examples;
- Aveli registered as a real-world application;
- Example and Application glossary concepts.

### Changed

- methodology evolution distinguishes synthetic exploration from real-world application evidence;
- ADR-001 uses Aveli as application evidence and synthetic examples to demonstrate portability.

---

## v0.1.1 — Presentation Pass

Added public-facing visual presentation, the SSAD model diagrams, and ADR-001.

---

## v0.1.0 — Foundation

Initial independent formalization of SSAD:

- methodology definition;
- Knowledge Architecture;
- Analysis Workflow;
- Change Model;
- core principles;
- evidence and maturity model;
- roles and stewardship;
- construction and change workflows;
- verification quality gates;
- maintenance workflow.
