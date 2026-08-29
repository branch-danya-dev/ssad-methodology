<div align="center">

# SSAD

### System-Structured Analysis Documentation

**A system-oriented methodology for building, organizing, verifying, and evolving system-analysis knowledge.**

![Version](https://img.shields.io/badge/version-v0.3.0-blue)
![Status](https://img.shields.io/badge/status-evolving-orange)
![Applications](https://img.shields.io/badge/real--world%20applications-1-success)

[Русская версия](README.ru.md)

</div>

---

## The idea

Most documentation repositories are organized around **artifact types**:

```text
requirements/
diagrams/
api/
security/
database/
```

Real systems are not.

A single change can cross product rules, data ownership, interfaces, runtime components, integrations, security, acceptance, and verification.

> **SSAD organizes knowledge around the system itself: its responsibilities, boundaries, owners, dependencies, and change impact.**

<p align="center">
  <img src="assets/ssad-model.svg" alt="SSAD model: Knowledge Architecture, Analysis Workflow, Change Model" width="100%">
</p>

---

## Three models, one knowledge lifecycle

| Model | Question | Focus |
|---|---|---|
| **Knowledge Architecture** | Where does knowledge belong? | perspectives, canonical ownership, references, synthesis |
| **Analysis Workflow** | How is knowledge discovered and stabilized? | evidence, boundaries, ownership, modeling, verification |
| **Change Model** | How does knowledge evolve with the system? | Change Surface, impact analysis, traceability, maintenance |

SSAD is not only a repository structure and not only an analysis process. It is a way to manage **system knowledge through its lifecycle**.

---

## Choose a playbook

The methodology now includes practical playbooks for the three most common starting conditions.

```text
Do you have a real existing system?
        │
        ├── NO
        │    ↓
        │  NEW SYSTEM
        │
        └── YES
             │
             ├── Is its analytical baseline trustworthy?
             │        │
             │        ├── NO → EXISTING SYSTEM
             │        │
             │        └── YES
             │              ↓
             └─────────── CHANGE
```

| Situation | Playbook |
|---|---|
| new product, service, plugin, platform, or major greenfield subsystem | [`playbooks/new-system.md`](playbooks/new-system.md) |
| running system with incomplete, fragmented, stale, or implementation-shaped knowledge | [`playbooks/existing-system.md`](playbooks/existing-system.md) |
| new feature, rule, integration, technology replacement, or architecture change against an existing baseline | [`playbooks/change.md`](playbooks/change.md) |

Quick decision guide: [`playbooks/quick-reference.md`](playbooks/quick-reference.md)

> **Playbooks guide the work. They do not prescribe the final repository tree.**

---

## Examples and real-world applications

SSAD deliberately separates **examples** from **applications**.

### Examples

`examples/` contains synthetic systems created specifically to explain or exercise the methodology.

| Example | System shape | Main SSAD idea | Depth |
|---|---|---|---|
| [Mobile Application](examples/mobile-application/) | client + backend + local/server data | local/server ownership and synchronization boundary | focused |
| [Desktop Plugin](examples/desktop-plugin/) | plugin + host application + filesystem | full SSAD workflow, system-shaped baseline, Change Surface | **worked** |
| [Event-Driven Platform](examples/event-driven-platform/) | services + messaging + data + operations | distributed ownership and asynchronous contracts | focused |

The Desktop Plugin worked example demonstrates:

```text
analysis workflow
        ↓
walkthrough/
        ↓
stable knowledge
        ↓
baseline/
        ↓
new request
        ↓
changes/dms-upload/
```

### Applications

`applications/` contains **real projects actually documented using SSAD**.

Current real-world application:

**Aveli** — local-first mobile workspace  
[`applications/aveli/`](applications/aveli/) · [full project repository](https://github.com/branch-danya-dev/aveli-system-analysis)

> **Examples illustrate SSAD. Applications exercise SSAD in real work.**

---

## Core principles

| | |
|---|---|
| **Documentation mirrors the system.** | Structure follows real responsibilities and boundaries. |
| **Ownership comes before detail.** | Contracts, schemas, states, and technology placement depend on ownership. |
| **Perspectives are required; folder templates are not.** | Different systems may require different physical structures. |
| **Canonical knowledge has one owner.** | Context may repeat; competing truth should not. |
| **Storage is hierarchical; knowledge is graph-based.** | Folders provide ownership; references express relationships. |
| **Evidence beats architectural preference.** | Existing-system truth is derived from evidence, not aesthetic preference. |
| **System documentation is a synthesis layer.** | Cross-component knowledge is synthesized rather than duplicated. |
| **Changes start with their Change Surface.** | Impact is mapped before downstream detail is rewritten. |

Full set: [`specification/core-principles.md`](specification/core-principles.md)

---

## How analysis works

<p align="center">
  <img src="assets/analysis-workflow.svg" alt="SSAD analysis workflow" width="100%">
</p>

```text
DISCOVER → BOUND → OWN → MODEL → CONNECT → SYNTHESIZE → VERIFY → STABILIZE → EVOLVE
```

The sequence describes **knowledge dependencies, not waterfall phases**.

Detailed workflow: [`workflow/construction.md`](workflow/construction.md)  
Worked example: [`examples/desktop-plugin/walkthrough/`](examples/desktop-plugin/walkthrough/)

---

## Change analysis

For an existing baseline, SSAD begins a material change with the **Change Surface**.

```text
Change Request
      ↓
Change Surface
      ↓
Affected Owners
      ↓
Boundary / Data / Interface Impact
      ↓
Component / Technology / Trust Impact
      ↓
Acceptance + Traceability
      ↓
Verification
      ↓
Stable
```

Detailed process: [`workflow/change-analysis.md`](workflow/change-analysis.md)  
Operational playbook: [`playbooks/change.md`](playbooks/change.md)  
Worked change: [`examples/desktop-plugin/changes/dms-upload/`](examples/desktop-plugin/changes/dms-upload/)

---

## Methodology evolution

```text
Observed problem
      ↓
Example exploration and/or real application evidence
      ↓
Proposal
      ↓
Validation
      ↓
Accept / Reject / Revise
      ↓
Specification update
```

The first accepted methodology decision is:

**ADR-001 — Perspectives Over Folder Templates**

[`decisions/ADR-001-perspectives-over-folder-templates.md`](decisions/ADR-001-perspectives-over-folder-templates.md)

---

## Start here

| If you want to... | Read |
|---|---|
| understand SSAD quickly | [`specification/methodology.md`](specification/methodology.md) |
| see the principles | [`specification/core-principles.md`](specification/core-principles.md) |
| **use SSAD on a new system** | [`playbooks/new-system.md`](playbooks/new-system.md) |
| **reconstruct an existing system** | [`playbooks/existing-system.md`](playbooks/existing-system.md) |
| **analyze a change** | [`playbooks/change.md`](playbooks/change.md) |
| follow SSAD from discovery to Stable | [`examples/desktop-plugin/walkthrough/`](examples/desktop-plugin/walkthrough/) |
| inspect stable system-shaped documentation | [`examples/desktop-plugin/baseline/`](examples/desktop-plugin/baseline/) |
| inspect real-world usage | [`applications/`](applications/) |
| run a quality gate | [`workflow/verification.md`](workflow/verification.md) |
| follow methodology evolution | [`decisions/`](decisions/) and [`proposals/`](proposals/) |

---

## What SSAD does not replace

SSAD does not replace UML, BPMN, C4, ADRs, OpenAPI, database schemas, source code, tests, product management, operational runbooks, or architecture governance.

It defines **how those forms of knowledge can be owned, connected, constructed, verified, and evolved around the system itself**.

---

## Current maturity

```text
SSAD v0.3.0

Foundation                    ✓
Public presentation           ✓
Examples / applications       ✓
Worked example                ✓
Change Surface walkthrough    ✓
Operational playbooks         ✓

Core playbooks:
new system
existing system
change

Real-world applications:
Aveli

Next:
extract reusable templates from repeated playbook outputs
→ validate playbooks on additional real-world applications
→ machine-readable metadata
→ automated consistency checks
```
