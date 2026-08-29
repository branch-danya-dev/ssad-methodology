# Interfaces

[Русская версия](README.ru.md)

Interfaces answer:

> **How do two responsibility zones exchange data, commands or results, and which contract exists between them?**

An interface may be HTTP, an event, function call, file, queue, IPC or another mechanism. The transport is secondary to the responsibility boundary and its semantics.

## Questions

```text
Which responsibility zones are connected?
Who is consumer and provider?
Who owns the contract semantics?
What does the request/event mean?
Which inputs are required?
How are success and errors represented?
Which timeout, retry, ordering or idempotency guarantees exist?
How is compatibility maintained?
What is a breaking change?
```

## Interface vs Integration vs Flow

```text
Interface
= contract across one boundary

Integration
= interaction with an external ownership boundary

Flow
= end-to-end scenario across multiple responsibilities/interfaces
```

A schema is only part of the interface. A useful contract also defines purpose, ownership, semantics, errors, guarantees and compatibility rules.
