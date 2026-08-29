# Storage Hierarchy

The physical structure of knowledge should help readers navigate the system.

> **Storage is hierarchical. Knowledge is connected as a graph.**

## Problem

If structure is organized only by artifact type — requirements, diagrams, APIs, security — knowledge about one responsibility zone becomes scattered across many locations.

Readers then have to reconstruct the system themselves.

## Principle

The physical hierarchy should, where useful, reflect stable responsibility areas of the real system.

For example:

```text
business/
backend/
frontend/
database/
integrations/
system/
```

This is not a mandatory SSAD template. Another system may require a completely different decomposition.

## Do not copy the source tree mechanically

Documentation structure may partially resemble code structure, but that is not the goal. A section deserves its own place because it represents a meaningful responsibility, boundary, decision area or knowledge owner.

## Responsibility at every level

Each directory should answer one major question. Each document should answer one bounded question.

If the purpose of a directory cannot be explained in one sentence, its responsibility is probably too diffuse.

## Size is not complexity

Ten small files with clear ownership may be easier to understand than one 1,500-line document.

The goal is not to minimize file count. It is to minimize the cost of finding, reading and changing knowledge.

## Check

For every element in the hierarchy ask:

```text
Why does this area exist?
What responsibility does it represent?
Why does this knowledge belong here?
Can a reader find it without understanding the entire repository?
```

Next: [`../knowledge-links/`](../knowledge-links/).
