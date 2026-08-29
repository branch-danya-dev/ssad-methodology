# Changelog

## Unreleased — Reader-first methodology

Completed the migration from the research-oriented SSAD structure to one active reader-first methodology tree.

### Added

- `01-foundation/` — core SSAD principles;
- `02-workflow/` — real system-analyst delivery workflow;
- `03-analysis/` — boundaries, responsibilities, ownership, local models and cross-boundary analysis;
- `04-knowledge-structure/` — canonical ownership, hierarchy, links and progressive depth;
- `05-collaboration/` — contribution, validation, decision resolution and feedback loops;
- `06-change/` — impact analysis, compatibility and selective reopening;
- `07-practice/` — task-based daily checklists;
- `08-examples/` — real-world Aveli validation slices.

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
