# Progressive Depth

SSAD should let readers understand the system at the depth they need without forcing everyone through the entire repository.

## Principle

```text
SYSTEM OVERVIEW
↓
RESPONSIBILITY AREA
↓
BEHAVIOR / CONTRACT / DATA
↓
TECHNOLOGY
↓
TECHNOLOGY USAGE
↓
IMPLEMENTATION EVIDENCE
```

The deeper the level, the more detail it contains and the narrower its audience becomes.

## Why this matters

A newcomer usually needs context and a system map. A backend developer needs behavior and contracts. A change analyst needs ownership, flows and dependencies. QA needs states, edge cases and failure semantics.

The same knowledge base should support all of these reading modes.

## Overview should not duplicate detail

The top level should explain what the system is, which major responsibility areas exist, how they relate and where to go next. It should not copy every local rule and contract.

## Local self-sufficiency

A document should contain enough context to understand the local topic without opening ten neighboring files, but it should not become a copy of the whole system.

Useful formula:

```text
LOCAL CONTEXT
+
CANONICAL FACTS OF THIS OWNER
+
LINKS TO FOREIGN KNOWLEDGE
```

## Quality criterion

A repository may be physically large but should **feel small**: at any moment the reader sees only the slice of knowledge needed for the current question.

Next: [`../../05-collaboration/`](../../05-collaboration/).
