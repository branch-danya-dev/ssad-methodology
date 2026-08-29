# Changelog

## v0.1.2 — Examples and Applications

Separated synthetic methodology examples from real-world applications.

### Added

- `examples/` as a home for fictional or intentionally simplified systems;
- `applications/` as a registry of real projects actually documented using SSAD;
- three synthetic examples:
  - mobile application;
  - desktop plugin;
  - event-driven platform;
- Aveli migrated from the old case model into `applications/aveli/`;
- glossary definitions for Example and Application.

### Changed

- methodology evolution now distinguishes low-cost exploration on synthetic examples from evidence gathered through real-world applications;
- ADR-001 now references Aveli as a real-world application and uses synthetic examples to demonstrate portability;
- proposals, templates, and playbooks no longer use the ambiguous "case" terminology;
- root README now explains the Examples / Applications model;
- current maturity updated to v0.1.2.

### Removed

- `cases/` model;
- empty `LICENSE.txt` until an explicit licensing decision is made.

---

## v0.1.1 — Presentation Pass

Public-facing presentation pass over the v0.1 foundation.

### Added

- visual overview of the three SSAD models;
- visual dependency-driven analysis workflow;
- localized EN/RU rendered diagrams and PlantUML sources;
- ADR-001: Perspectives Over Folder Templates;
- explicit decision index and methodology-decision lifecycle.

### Changed

- root README reorganized around problem → idea → models → workflow → applications → navigation;
- presentation assets explicitly separated from normative methodology content.

---

## v0.1.0 — Foundation

Initial independent formalization of SSAD.

### Added

- methodology definition;
- Knowledge Architecture + Analysis Workflow + Change Model framing;
- core principles;
- evidence and maturity model;
- roles and stewardship;
- construction workflow;
- Change Surface and change-analysis workflow;
- verification quality gates;
- maintenance workflow;
- first real project application: Aveli;
- methodology findings derived from Aveli.

### Deliberately Deferred

- reusable templates;
- practical playbooks;
- machine-readable metadata;
- automated linting;
- additional real-world applications;
- stable v1.0 specification.
