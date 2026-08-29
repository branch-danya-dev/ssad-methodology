# Canonical Ownership

Canonical ownership answers:

> **Where is the primary source of truth for a specific piece of system knowledge?**

SSAD does not require all knowledge to live in one document. But every meaningful fact should have **one canonical knowledge owner**.

## Problem

When the same rule is independently described in several places, drift appears and readers no longer know which version is authoritative.

## Principle

```text
ONE FACT
   ↓
ONE CANONICAL OWNER
   ↓
MANY CONTEXTUAL REFERENCES
```

If backend Access owns the decision about entitlement, the access rule should be canonical there. Frontend, billing flows and QA scenarios may repeat local context, but should reference the canonical rule.

> **Do not duplicate knowledge. Duplicate context when useful.**

## How to choose the owner

Ask:

```text
Who makes the decision?
Who stores authoritative state?
Who is responsible for correctness?
Where should a change to this knowledge be made first?
```

Physical location should follow logical ownership, not the place where an author first needed the information.

## Contextual repetition is allowed

A local document may say how it consumes another area's rule and then link to the canonical source. The repeated context should not become a second independent source of truth.

## Check

For every significant statement you should be able to answer:

- where its canonical source is;
- why it belongs there;
- who must update it when the system changes;
- which other documents only consume it.

Next: [`../storage-hierarchy/`](../storage-hierarchy/).
