# Aveli · bounded offline trust

## System question

How can a user continue professional work without permanent connectivity without turning the local client into a permanent source of truth for access rights?

## SSAD reasoning

Offline behavior is not merely “show cached data when the network is unavailable.”

The system must define explicitly:

```text
what is stored locally;
why it can be trusted;
how long that trust remains valid;
what happens after expiration;
what happens to user data;
how the system recovers when connectivity returns.
```

## Aveli

The professional workspace is stored locally and normal work does not require permanent backend availability.

At the same time, workspace access remains a server-owned decision.

The client may persist a previously verified `AccessState` in protected storage.

```text
Backend available
→ obtain verified AccessState
→ persist trusted snapshot

Backend / network unavailable
→ evaluate snapshot validity
→ temporarily continue or require connectivity
```

## Trust window

A trusted snapshot does not have infinite lifetime.

If the server returns `nextVerificationRequiredAt`, that value defines the next mandatory verification time.

The current implementation also contains a fallback period for cases where no explicit server deadline exists and policy permits it.

The concrete fallback value is an implementation detail, not a permanent business constant.

## Critical invariant

```text
network unavailable
≠
workspace deleted

access verification expired
≠
workspace deleted
```

Expiration of access trust affects feature availability, but it does not change ownership or lifecycle of professional workspace data.

This prevents two independent questions from being collapsed into one:

```text
May I open the workspace now?

and

Do my local professional data still exist?
```

## Failure and recovery

When connectivity returns, re-verification may happen through:

```text
user retry
app resume
billing reconciliation
access refresh
```

The offline policy therefore contains not only a happy path but also:

```text
trust source
validity window
expiration behavior
failure state
recovery path
```

## Canonical Aveli source

https://github.com/branch-danya-dev/aveli-system-analysis/blob/main/system/flows/offline-workspace.md

Local implementation details belong to the relevant frontend/backend areas while the cross-component invariant belongs at system level.

## SSAD links

- [`../../03-analysis/trust/README.md`](../../03-analysis/trust/README.md)
- [`../../03-analysis/failures/README.md`](../../03-analysis/failures/README.md)
- [`../../03-analysis/states/README.md`](../../03-analysis/states/README.md)
- [`../../03-analysis/synthesis/README.md`](../../03-analysis/synthesis/README.md)

## What the complete Aveli case demonstrates

The three slices form one reasoning path:

```text
SYSTEM STRUCTURE
↓
CANONICAL OWNERSHIP
↓
CROSS-BOUNDARY FLOW
↓
TRUST & FAILURE POLICY
↓
SYSTEM SYNTHESIS
```

That is the purpose of examples in SSAD: not to provide another template, but to demonstrate how the analytical principles work in a real system.
