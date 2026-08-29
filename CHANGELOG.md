# Changelog

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
- root README now includes a playbook chooser;
- methodology specification now distinguishes the normative workflow from operational playbooks;
- current maturity updated to `v0.3.0`.

### Design Decision

The methodology deliberately starts with three core playbooks:

```text
new system
existing system
change
```

Integration changes, architecture changes, technology replacements, migrations, and provider changes are treated as branches until real-world applications demonstrate that their work dependency structure is materially different.

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
