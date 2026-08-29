# Flows

[Русская версия](README.ru.md)

A flow is an end-to-end scenario that crosses multiple responsibility zones, interfaces, and sometimes external integrations.

## Main question

> How does a user or system action move through the system from trigger to observable result?

Local models may all be correct individually while the overall system is still inconsistent at the boundaries. That is why SSAD uses end-to-end flows after local analysis.

## Core model

```text
Trigger
  ↓
Zone A
  ↓ interface
Zone B
  ↓ integration
External system
  ↓ callback/evidence
Zone C
  ↓
Observable outcome
```

A flow does not replace local models. It checks whether they compose into one coherent scenario.

## Track at every step

- who owns the action;
- what data is transferred;
- which contract is used;
- which state is read;
- which state changes;
- where a decision is made;
- where failure may happen;
- what is observable outside the step.

## Example: subscription purchase

```text
User
 ↓
Frontend
 ↓ purchase request
RevenueCat
 ↓ purchase evidence
Backend Billing
 ↓ reconciliation
Access
 ↓ effective access
Frontend
 ↓ refreshed access state
User sees unlocked feature
```

This exposes questions about delayed callbacks, backend outages, authority, duplicate processing, and recovery after partial failure.

## Method

```text
1. Define the trigger and expected observable outcome.
2. List responsibility zones in order.
3. Mark each interface or integration boundary.
4. Mark ownership of decisions and state.
5. Mark state changes.
6. Add alternative paths.
7. Add failure points.
8. Check end-to-end invariants.
```

Model at least:

```text
main flow
alternative flow
failure/recovery flow
```

## Flow and sequence diagrams

A sequence diagram is a useful representation, but it is not the knowledge itself. Actors, ownership, contracts, decisions, state changes and failure behavior should be understood before the diagram is drawn.

## Result

A good flow preserves causality:

```text
trigger
→ interaction
→ decision
→ state change
→ next interaction
→ observable result
```

and explains what happens when any step deviates.

## Common mistakes

- drawing a sequence diagram without ownership;
- showing only services and calls rather than decisions and state;
- documenting only the happy path;
- duplicating canonical local knowledge inside the flow.

## Verification

A flow is sufficiently complete when any step can be explained in terms of why it occurs, who initiates it, which contract applies, what state is used, who decides, and what happens on failure.

Next: [`../trust/`](../trust/).
