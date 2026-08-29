# SSAD Core Principles

[Русская версия](core-principles.ru.md)

## P-01 — Documentation Mirrors the System
Documentation follows real responsibilities and boundaries before analyst artifact categories.

## P-02 — Ownership Before Detail
Do not stabilize contracts, schemas, state models, technology placement, or UI behavior before the relevant responsibility owner is understood.

## P-03 — Perspectives, Not Folder Templates
Important analytical questions are mandatory. Identical repository trees are not.

## P-04 — One Canonical Owner
A material fact should have one canonical source.

## P-05 — Context May Repeat; Canonical Truth Should Not
Cross-reference related knowledge instead of creating competing definitions.

## P-06 — Storage Is Hierarchical; Knowledge Is Graph-Based
Directories provide ownership and navigation. Cross-references represent real system relationships.

## P-07 — Data Progresses from Ownership to Persistence
```text
ownership → conceptual → logical → physical → lifecycle
```

## P-08 — Technology Is an Analytical Object
Technology should be connected to responsibility, usage, dependencies, constraints, criticality, and replaceability.

## P-09 — Technology Ownership Follows Responsibility
A technology belongs canonically to the perspective whose responsibility it primarily realizes.

## P-10 — Internal Interfaces Are Not External Integrations
Internal component contracts and external system boundaries are different analytical objects.

## P-11 — System Is a Synthesis Layer
Cross-component knowledge belongs to the nearest common system-level owner.

## P-12 — Evidence Beats Architectural Preference
Current-system documentation prefers trustworthy evidence to a cleaner imagined architecture.

## P-13 — Dependency Before Sequence
Workflow stages describe what depends on what; they are not waterfall phases.

## P-14 — Change Starts with Change Surface
Identify affected owners, boundaries, contracts, data, and invariants before detailing a change.

## P-15 — Unknowns Stay Explicit
Important uncertainty remains `OPEN` until resolved or classified.

## P-16 — Stable Means Verified Enough to Be Upstream
A document is Stable because it can safely act as canonical input, not because it is long or polished.
