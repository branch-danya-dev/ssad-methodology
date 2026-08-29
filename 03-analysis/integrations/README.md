# Integrations

[Русская версия](README.ru.md)

An integration is not merely an external API call. It is an interaction across an ownership boundary where part of the behavior or state is controlled by another system.

## Main question

> What happens when our system depends on an external owner of data, decisions, or behavior?

## Why this is a separate analytical perspective

An internal interface connects responsibility zones inside the analyzed system. An integration crosses an external ownership boundary.

That changes the analysis:

- we do not control the external implementation;
- the external contract may evolve independently;
- the external system may be unavailable;
- received data may be delayed or incomplete;
- external state may diverge from internal state;
- the authority for the final decision must be explicit.

## Core model

```text
Our system
   |
   | request / event / evidence
   v
External system
   |
   | response / callback / state
   v
Our system
   |
   v
Internal decision / reconciliation
```

The key distinction is:

```text
external evidence
!=
internal authority
```

## Example: RevenueCat

RevenueCat may report purchase or subscription state, but that does not automatically make it the owner of effective user access inside Aveli.

```text
RevenueCat
   |
   | purchase/subscription evidence
   v
Billing
   |
   | reconciliation
   v
Access
   |
   v
Effective user access
```

## Questions to answer

For every integration determine:

1. Where is the ownership boundary?
2. What crosses it: command, data, event, confirmation, evidence, canonical state?
3. Who makes the final decision?
4. How is state synchronized?
5. What happens when states diverge?
6. What happens when the external system is unavailable?
7. What guarantees does the contract provide?

Typical mechanisms include request-response, callback/webhook, polling, event streams, retries and manual reconciliation.

## Method

```text
1. Find the external ownership boundary.
2. Identify what crosses it.
3. Identify the authority for the final decision.
4. Describe the normal path.
5. Describe divergence and reconciliation.
6. Describe outage and degraded behavior.
7. Capture contract guarantees and limits.
```

## Result

A good integration model should make it possible to explain:

```text
what the external system knows;
what it can change;
what it reports to us;
what we trust;
what we decide internally;
how consistency is restored;
what happens on failure.
```

## Common mistakes

- treating an integration as just an API;
- making an external service an authority without an explicit decision;
- documenting only the happy path;
- confusing stale state with authoritative state.

## Verification

The integration is described well enough when the team can clearly answer who owns each state, what is evidence, who decides, how reconciliation works, and what happens on timeout, duplicate, delay and outage.

Next: [`../flows/`](../flows/).
