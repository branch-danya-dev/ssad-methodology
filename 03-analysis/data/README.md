# Data

[Русская версия](README.ru.md)

Data answers:

> **Which information exists in the system, who owns it, where is authoritative state, and how does it evolve?**

SSAD treats data as part of system responsibility, not merely as database tables.

## Analysis order

```text
OWNERSHIP
↓
CONCEPTUAL MODEL
↓
LOGICAL MODEL
↓
PHYSICAL STORAGE
↓
CONSTRAINTS / LIFECYCLE / MIGRATIONS
```

Start with meaning and ownership, then move toward storage.

## Questions

```text
What does this data mean?
Who is the authoritative owner?
Who can create or mutate it?
Who only reads or caches it?
Which values are derived?
Which relationships and constraints exist?
How is the data created, changed, archived and deleted?
How are copies synchronized?
What happens on conflicts or owner unavailability?
```

A useful data model separates conceptual, logical and physical concerns and makes lifecycle, copies and conflict policy explicit.
