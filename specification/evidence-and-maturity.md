# Evidence and Maturity

[Русская версия](evidence-and-maturity.ru.md)

## Evidence Status

| Status | Meaning |
|---|---|
| `VERIFIED` | Supported directly by trustworthy evidence |
| `INFERRED` | Reasonable conclusion derived from available evidence |
| `OPEN` | Requires confirmation, decision, or further investigation |

Evidence may include stakeholder decisions, source code, API contracts, schemas, configuration, provider contracts, tests, runtime behavior, logs, and existing documentation.

## Current vs Target State

Never mix current verified behavior with proposed target behavior without marking the difference.

## Maturity

```text
Draft
→ Baseline
→ Stable
```

- **Draft** — discovery is active; ownership or meaning may still change materially.
- **Baseline** — stable enough to become upstream input for deeper analysis.
- **Stable** — sufficiently cross-checked to act as canonical knowledge.

## Reopening

Stable knowledge may be reopened when new evidence appears, the system changes, an upstream decision changes, an external contract changes, or an assumption is invalidated.

Maturity is not permanence.
