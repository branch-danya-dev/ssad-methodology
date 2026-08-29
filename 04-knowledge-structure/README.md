# 04 · Knowledge Structure

[Русская версия](README.ru.md)

This section answers:

> **How do analysis results become a knowledge base where readers can find local truth, identify its owner and trace its relationships to the rest of the system?**

SSAD does not define a universal folder tree. Structure is derived from the real system, its responsibility zones and ownership.

## Core path

```text
ANALYSIS RESULT
      ↓
CANONICAL OWNER
      ↓
STORAGE HIERARCHY
      ↓
KNOWLEDGE LINKS
      ↓
PROGRESSIVE DEPTH
      ↓
TEAM CONSUMPTION
```

Physical storage and logical relationships solve different problems:

```text
Storage is hierarchical.
Knowledge is connected as a graph.
```

## Topics

1. [`canonical-ownership/`](canonical-ownership/) — where the primary source of truth lives and why one fact should have one canonical owner;
2. [`storage-hierarchy/`](storage-hierarchy/) — how to structure knowledge around system responsibilities without mechanically copying the source tree;
3. [`knowledge-links/`](knowledge-links/) — how to connect local knowledge to dependencies, flows, interfaces, decisions and change surface without duplicating truth;
4. [`progressive-depth/`](progressive-depth/) — how to give newcomers an overview while allowing experts to jump directly to the needed depth.

## Core principle

> **Do not duplicate knowledge. Duplicate context when useful.**

A local document may explain why another area's rule matters here, while the canonical definition remains with its owner.

## System-shaped does not mean source-shaped

A structure such as:

```text
business/
backend/
frontend/
database/
integrations/
system/
```

may be useful when these areas really represent the responsibilities of the analyzed system.

It is not an SSAD template. Another system may require another decomposition.

The criterion is responsibility and ownership clarity, not similarity to code structure.

## A good knowledge base should answer

```text
Where is the canonical fact?
Why does it belong there?
Who owns it?
What local context is needed here?
What other knowledge is it related to?
How deeply should I read for the current question?
```

## Quality criterion

A repository may contain hundreds of files and still be simple if readers never need to understand hundreds of files at once.

> Good knowledge architecture makes a large repository feel small.

Next: [`05-collaboration/`](../05-collaboration/).
