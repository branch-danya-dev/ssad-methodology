# API / contract checklist

[Русская версия](README.ru.md)

Use this when designing or reviewing an API or interface contract.

Start with semantics before JSON:
- responsibility and purpose;
- initiator and owner;
- resource/command/event meaning;
- request fields and validation;
- response meaning;
- explicit error semantics;
- resulting state;
- idempotency;
- versioning and compatibility.

For meaningful errors define:

```text
Condition
Meaning
Protocol status
Machine-readable code
Client reaction
Retryability
Resulting state
```

Minimum output:

```text
Purpose
Owner
Operation semantics
Request contract
Response contract
Errors
State effects
Idempotency
Compatibility rules
Examples
```

Go deeper:
- [`03-analysis/interfaces`](../../03-analysis/interfaces/)
- [`03-analysis/behavior`](../../03-analysis/behavior/)
- [`03-analysis/states`](../../03-analysis/states/)
- [`06-change/compatibility-risk`](../../06-change/compatibility-risk/)
