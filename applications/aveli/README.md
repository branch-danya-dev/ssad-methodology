# Aveli — Real-World SSAD Application

[Русская версия](README.ru.md)

> **Type:** real-world application  
> **System:** local-first mobile workspace  
> **Repository:** https://github.com/branch-danya-dev/aveli-system-analysis

## Why Aveli Belongs Here

Aveli is not a synthetic methodology example. It is a real system-analysis project whose documentation was structured and stabilized using SSAD.

The application exercised:

- business context, scope, rules, requirements, and traceability;
- local vs server-side data ownership;
- frontend/backend responsibility boundaries;
- internal interfaces vs external integrations;
- technology ownership;
- offline access and trust behavior;
- system-level synthesis;
- failure and release review;
- bilingual documentation;
- legacy-documentation migration;
- repository-wide quality gates.

## Final Analytical Perspectives

```text
business/
database/
backend/
frontend/
integrations/
system/
```

This structure is a consequence of Aveli's actual system shape. It is not a universal SSAD template.

## Methodology Impact

Work on Aveli produced or reinforced several SSAD rules:

- analytical perspectives are required; folder templates are not;
- ownership comes before dependent detail;
- data ownership should precede physical persistence detail;
- technology ownership follows the responsibility primarily realized;
- internal interfaces and external integrations must be separated;
- system-level knowledge works best as late synthesis;
- legacy refactoring requires an orphan-knowledge check;
- a repeatable analysis workflow should be explicit.

See [`methodology-findings.md`](methodology-findings.md).
