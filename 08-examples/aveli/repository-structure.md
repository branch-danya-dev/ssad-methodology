# Aveli · repository structure as a system model

## System question

How should analytical knowledge be organized so a reader knows where to find the canonical truth about a specific part of the system?

## SSAD reasoning

SSAD does not begin with a universal tree such as:

```text
requirements/
diagrams/
api/
security/
```

It begins by identifying real responsibility areas and then assigning knowledge ownership to them.

## Aveli

In Aveli, the natural top-level areas became:

```text
business/
database/
backend/
frontend/
integrations/
system/
```

This is not an SSAD template. It is the result of analyzing this particular system.

### What belongs to local areas

```text
business/
→ product context, requirements and rules

backend/
→ server behavior, account, auth, access, billing and API

frontend/
→ Flutter client, navigation, local state and offline behavior

database/
→ data ownership, models and physical storage

integrations/
→ external ownership boundaries
```

### Why `system/` exists

Decomposition is not enough.

Some knowledge belongs to no single component:

```text
end-to-end flows
cross-component trust
system invariants
multi-component evolution
system-level review
```

Aveli therefore uses `system/` as a synthesis area rather than a dumping ground for miscellaneous documents.

## Main lesson

```text
LOCAL OWNERSHIP
→ reduces reading scope

SYSTEM SYNTHESIS
→ prevents locally correct descriptions from contradicting one another
```

This is why “structure documentation like the system” does not mean “copy the source tree.”

The structure follows **analytical responsibility boundaries**, not source-code folders mechanically.

## Canonical Aveli sources

- `methodology.md` — knowledge-organization principles;
- `business/`, `backend/`, `frontend/`, `database/`, `integrations/` — local owners;
- `system/` — cross-component synthesis.

Full repository:

https://github.com/branch-danya-dev/aveli-system-analysis

## SSAD links

- [`../../04-knowledge-structure/storage-hierarchy/README.md`](../../04-knowledge-structure/storage-hierarchy/README.md)
- [`../../04-knowledge-structure/canonical-ownership/README.md`](../../04-knowledge-structure/canonical-ownership/README.md)
- [`../../03-analysis/synthesis/README.md`](../../03-analysis/synthesis/README.md)

Next: [`access-ownership.md`](access-ownership.md)
