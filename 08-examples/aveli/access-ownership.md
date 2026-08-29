# Aveli · access and billing ownership

## System question

Who in the system has the authority to make the final decision that a user may open the professional workspace?

A naive answer would be:

```text
RevenueCat reports an active subscription
→ therefore RevenueCat controls access
```

For SSAD, that is insufficient.

## Separate evidence from authority

In Aveli, external billing and internal access are different responsibilities.

```text
Store / RevenueCat
→ prove provider billing state

Aveli Backend
→ makes the final workspace access decision
```

RevenueCat is an important evidence source, but it is not the owner of the Aveli product decision.

## End-to-end flow

```text
Store purchase
        ↓
RevenueCat CustomerInfo
        ↓
Flutter
        ↓
POST /v1/billing/sync
        ↓
Aveli Backend
        ↓
provider-state verification through RevenueCat
        ↓
normalized subscription state
        ↓
AccessStatus calculation
        ↓
Frontend
```

There is also an asynchronous path:

```text
RevenueCat webhook
→ Aveli Backend
→ idempotency check
→ RevenueCat reconciliation
→ subscription snapshot
→ access evaluation
```

A webhook event type does not directly grant or revoke access.

## Why ownership cannot be inferred from data flow

Data crosses several systems:

```text
Store
→ RevenueCat
→ Backend
→ Frontend
```

But flow direction does not answer the authority question.

SSAD asks separately:

```text
Who provides evidence?
Who stores canonical normalized state?
Who makes the final decision?
Who only consumes the result?
```

For Aveli:

```text
billing evidence
→ Store / RevenueCat

normalized billing state
→ Backend

workspace access decision
→ Backend

access consumer
→ Frontend
```

## Important system invariant

A subscription is not the only possible access source.

The general access model may include:

```text
permanent access
manual entitlement
subscription
trial
```

Therefore the internal access model cannot be replaced by the single question “is the RevenueCat subscription active?”.

## Canonical Aveli sources

End-to-end flow:

https://github.com/branch-danya-dev/aveli-system-analysis/blob/main/system/flows/purchase-and-entitlement.md

Local knowledge is distributed between:

```text
integrations/revenuecat/
backend/billing/
system/flows/
```

This illustrates the principle:

> **Storage is hierarchical. Knowledge is graph-linked.**

## SSAD links

- [`../../03-analysis/ownership/README.md`](../../03-analysis/ownership/README.md)
- [`../../03-analysis/integrations/README.md`](../../03-analysis/integrations/README.md)
- [`../../03-analysis/flows/README.md`](../../03-analysis/flows/README.md)
- [`../../03-analysis/synthesis/README.md`](../../03-analysis/synthesis/README.md)

Next: [`offline-trust.md`](offline-trust.md)
