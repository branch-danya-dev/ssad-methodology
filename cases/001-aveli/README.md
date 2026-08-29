# Case 001 — Aveli

[Русская версия](README.ru.md)

## Case Type

```text
Local-first mobile application
Flutter client
NestJS backend
SQLite local workspace
PostgreSQL account/access backend
RevenueCat billing integration
```

Full project: https://github.com/branch-danya-dev/aveli-system-analysis

## Why Aveli Was Useful

Aveli contains boundaries that are easy to model incorrectly:

- local professional data vs server account/access data;
- frontend responsibility vs backend authority;
- internal frontend↔backend interface vs external billing providers;
- local offline behavior vs authoritative online access;
- storage engine vs runtime data-access technology;
- component knowledge vs whole-system synthesis.

## Construction History

```text
existing evidence
→ business baseline
→ data ownership split
→ frontend/backend responsibilities
→ integration boundaries
→ technology ownership correction
→ system synthesis
→ legacy documentation migration
→ whole-system quality gate
→ Stable baseline
```

## Final Analytical Perspectives

```text
business/
database/
backend/
frontend/
integrations/
system/
```

This structure is an Aveli result, not a mandatory SSAD template.

## What Was Validated

- system-shaped documentation;
- canonical ownership;
- dependency-driven construction;
- data ownership before persistence;
- technology ownership;
- internal vs external boundaries;
- evidence-first analysis;
- bilingual documentation;
- system synthesis;
- traceability;
- failure/release review;
- legacy documentation refactoring;
- final quality gate.

The case also produced changes to the methodology itself.

See [`methodology-findings.md`](methodology-findings.md).
