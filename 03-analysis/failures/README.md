# Failures

[Русская версия](README.ru.md)

Failure analysis does not ask only what can break. It asks:

> **How should the system behave when the normal scenario can no longer continue?**

If failure behavior is not designed explicitly, the team will still implement it, but the decision will be accidental and scattered across frontend, backend, integrations and infrastructure.

## Core model

```text
Expected interaction
       ↓
Failure condition
       ↓
Detection
       ↓
System decision
       ↓
Fallback / retry / reject / degrade
       ↓
Recovery or stable failed state
```

## Typical failure categories

Useful categories include dependency unavailable, timeout, invalid input, authorization failure, stale or conflicting state, duplicate request/event, partial completion, out-of-order event, missing or corrupted data, local storage failure, network loss, and unsupported contract/version.

## Questions to answer

For each meaningful failure point determine:

1. How is the problem detected?
2. Who owns the next decision?
3. Which state may already have changed?
4. Can the operation be retried safely?
5. Is compensation required?
6. What does the user or external consumer observe?
7. How does the system recover?
8. Is manual intervention required?

## Example: partially successful purchase

```text
RevenueCat confirms purchase
        ↓
Backend reconciliation starts
        ↓
Access update fails
```

A generic error response is not enough. The system must know whether the purchase really happened, whether reconciliation can be retried idempotently, what the frontend should display, how access will later be restored, and whether a pending state is required.

A more explicit model is:

```text
Purchase evidence received
        ↓
Reconciliation pending
        ↓
Retry / recovery process
        ↓
Access activated
```

or an explicit terminal failure with manual recovery when automation is impossible.

## Partial failure

Distributed scenarios require explicit intermediate-state analysis.

```text
A succeeded
B succeeded
C failed
```

Ask what the whole operation means now, what cannot be rolled back, what can be retried, and what the next participant needs to know.

## Retry semantics

Before introducing retries, understand idempotency, delayed completion of the original request, duplicate detection, identifiers, retry limits, and behavior after retries are exhausted.

## Fail open / fail closed

For access, security and critical constraints, explicitly choose behavior when the authority is unavailable:

```text
fail closed
→ reject without confirmation

fail open
→ temporarily allow without confirmation

bounded trust
→ use previously verified state only inside a defined window
```

## Method

```text
1. Take the main flow.
2. Find meaningful failure points.
3. Define detection for each.
4. Check state changes already committed.
5. Define retry/compensation/degraded behavior.
6. Define the observable result.
7. Define the recovery path.
8. Re-check system invariants after failure.
```

## Result

A good failure model explains what failed, how it was detected, which state remains, what happens next, what the consumer observes, and how consistency is restored.

## Common mistakes

- treating an HTTP 500 as the complete failure model;
- retrying non-idempotent operations blindly;
- describing errors without resulting state;
- leaving manual recovery implicit.

## Verification

Failure analysis is sufficient when the team knows detection, decision authority, resulting state, retry/compensation rules, observable behavior, recovery path, and the invariants that must still hold.

After failure analysis, return to [`../synthesis/`](../synthesis/) and re-check the system end to end.
