# Trust

[Русская версия](README.ru.md)

Trust in SSAD is not an abstract security property. It is an explicit system decision about **which data, states and decisions may be relied on, within which scope, and for how long**.

## Main question

> Why is this responsibility zone allowed to treat this value or decision as sufficiently reliable?

Trust appears whenever one zone consumes information owned or produced by another party.

Examples include frontend rendering from backend access state, backend accepting purchase evidence from RevenueCat, offline use of previously verified state, services consuming identity claims, and systems using cached data.

## Core model

```text
Source
  ↓ evidence/state
Consumer
  ↓ trust rule
Allowed decision or behavior
```

Always ask:

```text
Trusted for what?
Trusted by whom?
Trusted for how long?
Under which conditions?
How is trust revoked or refreshed?
```

## Trust is not ownership

A consumer may trust another zone's state without owning it.

```text
Backend owns effective access.
Frontend trusts backend access state for rendering UI.
```

## Trust is not freshness

Information may be valid when received and stale later. Analyze authority, freshness, validity window, revocation and revalidation separately.

## Example: bounded offline trust

Aveli may temporarily allow offline work based on the last verified access state.

```text
Backend confirms access
        ↓
Client stores trusted snapshot
        ↓
Offline period
        ↓
Trust remains valid only inside bounded window
        ↓
Revalidation required
```

Offline behavior should therefore be a result of an explicit trust policy, not an accidental property of caching.

## Method

```text
1. Find where a zone consumes another zone's state or decision.
2. Identify the authority.
3. Define the scope of trust.
4. Define the validity window.
5. Define refresh/revalidation.
6. Define revocation.
7. Define behavior when trust cannot be revalidated.
```

## Result

A good trust model explains who trusts whom, what is trusted, on which basis, within which limits, for how long, and how that trust ends.

## Common mistakes

- treating cached state as indefinitely trusted;
- confusing trust with ownership;
- omitting revocation paths;
- modeling offline behavior without explicit trust rules.

## Verification

Trust is sufficiently described when the team can explain the authority, the consumer, what decisions are allowed, when the state becomes stale, and what happens when revalidation is impossible.

Next: [`../failures/`](../failures/).
