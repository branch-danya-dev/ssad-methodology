# Knowledge Links

Hierarchy defines **where knowledge lives**. Links show **what it is related to**.

## Problem

A real system is not a tree. One flow may connect frontend, backend, billing, access, an external integration and local device state.

Trying to physically colocate all related knowledge quickly creates duplication or mixed responsibilities.

## Principle

```text
PHYSICAL STORAGE = HIERARCHY
KNOWLEDGE RELATIONSHIPS = GRAPH
```

A document stays with its canonical owner but may link to incoming and outgoing interfaces, dependent rules, related states, end-to-end flows, decisions, integrations and verification evidence.

## A link should explain the relationship

A weak link says only “See billing.md”. A useful link states why the dependency exists and what knowledge is consumed from the other owner.

## Context instead of a copy

When a local document needs another area's fact, use:

```text
local context
+
relationship explanation
+
canonical link
```

Do not copy the entire foreign section.

## Links support change analysis

Relationships make impact traceable:

```text
changed rule
↓
canonical owner
↓
consumers
↓
interfaces / flows / tests
↓
change surface
```

Links are therefore not merely navigation. They are part of the dependency model of system knowledge.

Next: [`../progressive-depth/`](../progressive-depth/).
