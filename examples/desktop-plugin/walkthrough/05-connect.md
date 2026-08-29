# 05 — CONNECT

[Русская версия](05-connect.ru.md)

## Question

How do the local models connect into one navigable knowledge graph?

At this stage, SSAD does not create new owners. It connects already-owned knowledge.

## Traceability

```text
BR-01
Source document must not be modified
    ↓
plugin/
export orchestration must use read/export host operations only
    ↓
host-application/
host export contract must not require document mutation
    ↓
verification
compare source document state before/after export
```

```text
BR-02
Each selected sheet is attempted independently
    ↓
plugin/
per-sheet loop + per-sheet result
    ↓
filesystem/
successful outputs remain persisted
    ↓
system/
partial success is a valid whole-job outcome
```

## Ownership Links

```text
Host sheet identity
    ↓ consumed by
Plugin export orchestration
    ↓ recorded in
Plugin-owned manifest content
    ↓ persisted by
Filesystem
```

## Technology vs Responsibility

No technology document is needed yet.

The example has conceptual responsibilities:

```text
host export capability
filesystem persistence
JSON manifest
```

but no meaningful technology decision has been made beyond the fictional scenario.

SSAD should not invent a `stack/` area merely to make the example look complete.

## Navigation Consequence

The stable repository will contain cross-links such as:

```text
business/BR-02
→ plugin/per-sheet behavior
→ filesystem/output retention
→ system/partial-success invariant
```

The physical tree remains hierarchical, while these relations form the knowledge graph.

## Output

The local models now explain not only **what** each owner knows, but **why** that knowledge exists and what depends on it.

Next: [`06-synthesize.md`](06-synthesize.md)
