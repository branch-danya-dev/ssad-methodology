# Changelog

## Unreleased — Reader-first methodology

Completed the migration from the research-oriented SSAD structure to one active reader-first methodology tree and expanded real-world validation across three materially different system shapes.

### Added

- `01-foundation/` — core SSAD principles;
- `02-workflow/` — real system-analyst delivery workflow;
- `03-analysis/` — boundaries, responsibilities, ownership, local models and cross-boundary analysis;
- `04-knowledge-structure/` — canonical ownership, hierarchy, links and progressive depth;
- `05-collaboration/` — contribution, validation, decision resolution and feedback loops;
- `06-change/` — impact analysis, compatibility and selective reopening;
- `07-practice/` — task-based daily checklists;
- `08-examples/aveli/` — product-shaped real-world validation through repository structure, access ownership and offline trust;
- `08-examples/enterprise-workplace-migration/` — transformation-shaped real-world validation through responsibility structure, global-status decomposition, distributed readiness evidence and ownership-aware technical projection;
- `08-examples/revit-rebar-autodim/` — host-application real-world validation through Revit authority boundaries, view-space geometry, semantic-vs-API references and generated-output ownership.

### Real-world validation

SSAD is now documented against three materially different real systems:

```text
Aveli
→ product-shaped software system

Enterprise Workplace Migration
→ distributed enterprise transformation

Rebar AutoDim
→ host-application automation inside Autodesk Revit
```

The important result is not that the repositories look similar. They do not.

```text
Aveli
→ business / backend / frontend / database / integrations / system

Enterprise Workplace Migration
→ system / workplace / readiness / planning / execution / exceptions / integrations / technical-projection

Rebar AutoDim
→ system / execution-context / geometry / references / layout / annotations / regeneration / revit-boundary / evidence
```

The same reasoning model produced three different knowledge architectures.

#### Enterprise migration evidence

The enterprise application demonstrated that:

- one global `migration_status` hid several independently owned state dimensions;
- distributed cross-team evidence did not remove the need for one explicit readiness owner;
- `MigrationSchedule` and `MigrationAttempt` required separate histories;
- technical installation success did not prove operational migration completion;
- canonical ownership changed the synthetic REST and PostgreSQL projections, not only the documentation tree;
- derived operational views could combine several owners without becoming a second source of truth.

#### Rebar AutoDim evidence

The host-application application demonstrated that:

- a host application can own native validity and execution mechanics without owning the plugin's analytical decisions;
- source model geometry and active-view context can have different owners while the plugin owns a derived canonical interpretation;
- semantic dimension targets must be separated from Revit `Reference` representations;
- API workarounds such as supporting detail geometry should realize existing meaning rather than become a new source of truth;
- `NOT_APPLICABLE` output and failed native realization are different system outcomes;
- plugin-generated annotation state has explicit ownership separate from source structural state;
- one-zone transaction scope can represent a meaningful failure-isolation boundary;
- repeated execution can be modeled as semantic convergence through full regeneration rather than element-ID preservation.

The roadmap now also marks host-application / embedded automation validation as completed.

### Quality pass

- expanded the English `Specification`, `Review`, `Grooming`, `Delivery Support`, `Verification` and `Knowledge Update` chapters so they preserve the same analytical responsibilities as the Russian versions instead of acting as short summaries;
- corrected the `03-analysis/` reading order so local and cross-boundary models are built before `synthesis`;
- added one complete recommended analysis route from boundaries through failures to system synthesis;
- normalized English terminology around `canonical owner`, `canonical knowledge`, `evidence`, `authority` and `responsibility area`;
- preserved the separation between workflow timing, analysis mechanics, knowledge architecture, collaboration mechanics and change analysis.

### Removed

The following migration-era top-level documentation trees were removed after their useful concepts were absorbed into the reader-first structure:

```text
applications/
cases/
decisions/
examples/
playbooks/
proposals/
specification/
templates/
workflow/
```

Also removed:

- `REPOSITORY-SETUP.md` — early bootstrap notes no longer needed by readers;
- empty `LICENSE.txt` — licensing has not yet been selected, so a zero-byte license was misleading.

`assets/` remains as supporting diagram infrastructure.

### Principle

> Historical documentation belongs in Git history once it has been superseded. The active tree should contain only current knowledge.

---

## v0.3.0 — Operational Playbooks

Introduced the first practical task-oriented guidance layer over the SSAD workflow.

### Added

- `playbooks/new-system.*`;
- `playbooks/existing-system.*`;
- `playbooks/change.*`;
- `playbooks/quick-reference.*`;
- a common playbook structure:
  - use conditions;
  - inputs;
  - steps;
  - outputs;
  - quality gates;
  - reopen conditions;
  - common failure modes;
  - exit criteria.

### Changed

- `playbooks/README.*` promoted from a placeholder to an operational entry point;
- root README included a playbook chooser;
- methodology specification distinguished the normative workflow from operational playbooks;
- current maturity was updated to `v0.3.0`.

### Design Decision

The methodology deliberately started with three core playbooks:

```text
new system
existing system
change
```

Integration changes, architecture changes, technology replacements, migrations, and provider changes were treated as branches until real-world applications could demonstrate that their work dependency structure was materially different.

### Methodology Principle Reinforced

> Playbooks guide the work. They do not prescribe the final repository tree.

---

## v0.2.0 — Worked Example

Introduced the first full synthetic SSAD walkthrough:

- analysis walkthrough;
- stable system-shaped baseline;
- Change Surface exercise;
- verification loop that reopens upstream knowledge.

---

## v0.1.2 — Examples and Applications

Separated synthetic methodology examples from real-world applications.

---

## v0.1.1 — Presentation Pass

Added public-facing visual presentation and ADR-001.

---

## v0.1.0 — Foundation

Initial independent formalization of SSAD.
