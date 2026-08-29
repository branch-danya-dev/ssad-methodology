# Desktop Plugin — Stable Baseline

[Русская версия](README.ru.md)

This directory is the **stable system-shaped output** of the analysis walkthrough.

It is intentionally not organized by workflow stage.

```text
baseline/
├── business/
├── plugin/
├── host-application/
├── filesystem/
└── system/
```

Each area owns a different class of canonical knowledge.

| Perspective | Canonical responsibility |
|---|---|
| [`business/`](business/) | product behavior, scope, business rules, acceptance |
| [`plugin/`](plugin/) | export orchestration and job-result semantics |
| [`host-application/`](host-application/) | source-document authority and host export boundary |
| [`filesystem/`](filesystem/) | physical persistence and collision safety |
| [`system/`](system/) | cross-perspective flow and invariants |

The temporal process that produced this baseline is documented separately in [`../walkthrough/`](../walkthrough/).

> **Walkthrough explains construction. Baseline expresses ownership.**
