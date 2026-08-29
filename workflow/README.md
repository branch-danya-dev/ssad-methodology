# SSAD Workflow

[Русская версия](README.ru.md)

SSAD workflow is not a software development lifecycle and not a mandatory sequence of meetings. It describes **knowledge dependencies**.

## System Construction

```text
DISCOVER → BOUND → OWN → MODEL → CONNECT → SYNTHESIZE → VERIFY → STABILIZE
```

See [`construction.md`](construction.md).

## Change Analysis

```text
Change Request → Change Surface → Impact Analysis → Knowledge Updates → Verification → Stable
```

See [`change-analysis.md`](change-analysis.md).

## Continuous Maintenance

```text
Implementation / decision change
→ canonical owner
→ knowledge update
→ reference check
→ traceability check
→ contradiction review
```

See [`maintenance.md`](maintenance.md).

## Core Rule

> **Build and change knowledge in dependency order. Do not confuse dependency with bureaucracy.**
