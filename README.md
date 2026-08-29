<div align="center">

# SSAD

### System-Structured Analysis Documentation

**A practical system analysis approach that structures knowledge around the real system, its boundaries and responsibilities — and explains essential ideas through theory, method, example and diagram.**

[Русская версия](README.ru.md)

</div>

---

## What this repository is

This repository is not a collection of document templates or a formal artifact archive.

It is designed as a **learning guide, reference and working route for system analysts**.

SSAD answers four practical questions:

```text
How should I think?
→ principles

How should I work?
→ real system analyst workflow

How should I analyze a system?
→ boundaries, responsibility, ownership, data, behavior, interfaces and connections

How should I preserve knowledge?
→ documentation shaped by the system itself
```

> **Structure knowledge like the system. Explain important decisions through practice.**

---

## Learning path

```text
01. FOUNDATION
Why does the approach exist?
        ↓
02. WORKFLOW
How does a system analyst actually work?
        ↓
03. ANALYSIS
How do we decompose and reason about a system?
        ↓
04. KNOWLEDGE STRUCTURE
How do we organize the resulting knowledge?
        ↓
05. COLLABORATION
How do the analyst, team and knowledge evolve together?
        ↓
06. CHANGE
How do we analyze changes to an existing system?
        ↓
07. PRACTICE
Which questions, checks and techniques help day to day?
        ↓
08. EXAMPLES
What does this look like in practice?
```

## Sections

| Section | Main question |
|---|---|
| [`01-foundation/`](01-foundation/) | What is SSAD and which principles support it? |
| [`02-workflow/`](02-workflow/) | What does a system analyst do from request intake to implementation verification? |
| [`03-analysis/`](03-analysis/) | How do we analyze boundaries, ownership, behavior, data, interfaces and flows? |
| [`04-knowledge-structure/`](04-knowledge-structure/) | How do we build a navigable system knowledge base? |
| [`05-collaboration/`](05-collaboration/) | How does SSAD interact with clients, analysts, developers, QA, architecture and integration teams? |
| [`06-change/`](06-change/) | How do we identify impact and safely change an existing system? |
| [`07-practice/`](07-practice/) | Which questions, checklists and working techniques help apply the approach? |
| [`08-examples/`](08-examples/) | How does SSAD look in synthetic and real-world systems? |

---

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

SSAD does not replace the real delivery process with an artificial lifecycle. It provides analytical methods and knowledge structure inside that process.

---

## Team ↔ SSAD

SSAD is not a private analyst notebook and knowledge is not simply handed off after specification.

The team consumes, reviews, challenges and enriches system knowledge. Implementation returns new evidence back into analysis.

> **System knowledge is not handed off to the team as a finished artifact. It is validated and evolved with the team.**

---

## How topics are taught

Important topics follow a common learning structure:

```text
Problem
→ Idea
→ Why
→ Questions
→ Method
→ Result
→ Example
→ Diagram
→ Common mistakes
→ Verification
```

This allows the repository to work both as a sequential learning guide and as a point-of-need reference.

---

## Real-world example

**Aveli** is a real system-analysis project whose knowledge base is structured around actual system boundaries and responsibilities:

https://github.com/branch-danya-dev/aveli-system-analysis

It is one of the primary sources used to demonstrate and validate SSAD.

---

## Restructuring status

The repository is transitioning from the research-oriented SSAD v0.3 structure to a **reader-first architecture**.

Existing `specification/`, `workflow/`, `playbooks/`, `applications/`, `decisions/` and related directories remain temporarily as migration sources. Their useful content will be moved into the new responsibility areas after the new structure is validated.
