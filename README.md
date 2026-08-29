<div align="center">

# SSAD

### System-Structured Analysis Documentation

**A practical system-analysis methodology for building, validating and maintaining knowledge around the real system, its boundaries and responsibilities.**

[Русская версия](README.ru.md)

</div>

---

## What SSAD is

SSAD is a **learning guide, reference and working route for system analysts**.

It does not prescribe a universal document tree. Instead it asks you to understand the system first and let the knowledge structure follow real responsibility boundaries.

> **Structure knowledge like the system. Keep one canonical owner for important facts. Connect local knowledge back into a coherent system view.**

```text
SYSTEM
  ↓
BOUNDARIES
  ↓
RESPONSIBILITIES
  ↓
OWNERSHIP
  ↓
LOCAL MODELS
  ↓
CONNECTIONS
  ↓
SYSTEM SYNTHESIS
```

## Learning path

| Section | Main question |
|---|---|
| [`01-foundation/`](01-foundation/) | Why does SSAD exist and what are its core principles? |
| [`02-workflow/`](02-workflow/) | What does a system analyst do from request intake to knowledge update? |
| [`03-analysis/`](03-analysis/) | How do we analyze boundaries, ownership, behavior, states, data, interfaces, integrations, flows, trust and failures? |
| [`04-knowledge-structure/`](04-knowledge-structure/) | Where should system knowledge live and how should it be connected? |
| [`05-collaboration/`](05-collaboration/) | How do people validate, challenge and evolve system knowledge together? |
| [`06-change/`](06-change/) | How do we analyze impact and safely change an existing system? |
| [`07-practice/`](07-practice/) | Which short checklists help in day-to-day analytical work? |
| [`08-examples/`](08-examples/) | What does the methodology look like on a real system? |

Recommended first read:

```text
Foundation
→ Workflow
→ Analysis
→ Knowledge Structure
→ Collaboration
→ Change
```

Use [`07-practice/`](07-practice/) when you already have a concrete task and need a quick route into the methodology.

## Real analyst workflow

```text
PRE-ANALYSIS
→ REQUIREMENTS
→ ANALYSIS & DESIGN
→ SPECIFICATION
→ REVIEW
→ GROOMING
→ DELIVERY SUPPORT
→ VERIFICATION
→ KNOWLEDGE UPDATE
```

The workflow is iterative. Review, implementation and verification may expose evidence that reopens earlier analysis.

## Knowledge architecture

SSAD separates storage from relationships:

```text
Hierarchy
→ where canonical knowledge lives

Links
→ how knowledge depends on other knowledge
```

> **Storage is hierarchical. Knowledge is graph-connected.**

A local document may repeat enough context to remain readable, but should link to the canonical owner instead of creating a second independent truth.

## Team ↔ SSAD

System knowledge is not a finished artifact handed from an analyst to developers.

```text
People
  ↕
System knowledge
  ↕
Implementation / QA / Operations
  ↓
Evidence
  ↺
Analysis and knowledge update
```

Different participants contribute different evidence and authority. Implementation itself is also a source of evidence.

## Real-world validation

The primary real-world case is **Aveli**:

https://github.com/branch-danya-dev/aveli-system-analysis

The compact learning route is available in [`08-examples/aveli/`](08-examples/aveli/).

Aveli is used to validate SSAD against real boundaries, local data, backend-controlled access, billing integrations, offline trust, failures and end-to-end flows.

## Repository shape

The current repository intentionally has one reader-first methodology structure:

```text
01-foundation/
02-workflow/
03-analysis/
04-knowledge-structure/
05-collaboration/
06-change/
07-practice/
08-examples/
assets/
```

`assets/` contains supporting diagram sources and rendered visuals. It is infrastructure, not a competing methodology section.

Historical restructuring material is preserved by Git history rather than as a second active documentation tree.
