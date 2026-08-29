# Example — Event-Driven Platform

[Русская версия](README.ru.md)

> **Status:** synthetic example  
> **Purpose:** demonstrate distributed ownership, asynchronous contracts, and an operations perspective.

## Scenario

A fictional order-processing platform receives orders, reserves inventory, requests payment, and emits fulfillment events.

Assumptions:

```text
Order service
Inventory service
Payment service
Message broker
Separate service databases
External payment provider
Container platform
Observability stack
```

## Possible SSAD Perspectives

```text
business/
services/
messaging/
data/
integrations/
operations/
system/
```

Again, the structure follows system responsibility rather than a mobile/web template.

## Ownership Example

```text
Order lifecycle
→ Order service

Inventory availability
→ Inventory service

Internal payment-attempt state
→ Payment service

External transaction state
→ payment provider

Message delivery infrastructure
→ messaging

Deployment / observability / recovery
→ operations
```

## Asynchronous Contract Example

Event:

```text
InventoryReserved
```

The event schema is not owned by "Kafka" as a technology.

Its semantic contract belongs to the system responsibility that publishes the fact, while messaging documentation owns transport behavior and infrastructure constraints.

This separates:

```text
business/system event meaning
≠
messaging technology
```

## Change Surface Example

Change request:

> Allow payment retries for 24 hours without releasing inventory.

Likely impact:

```text
Business rules       YES
Order service        YES
Inventory service    YES
Payment service      YES
Messaging            YES
Data lifecycle       YES
External integration YES
Failure/recovery     YES
Operations           MAYBE
System invariants    YES
```

## Intentionally Simplified

The example does not claim real Kafka topics, service code, schemas, SLAs, deployment manifests, or provider contracts.
