# Ownership checklist

[Русская версия](README.ru.md)

Use this when it is unclear who actually owns a state, fact or decision.

Ask:
- Who decides?
- Who stores the canonical state?
- Who may change it?
- Who only provides evidence?
- Who consumes the result?
- Who validates correctness?

Do not infer ownership from physical storage, UI display, request initiation or technical write access.

Minimum output:

```text
Knowledge/state
Canonical owner
Decision authority
Allowed writers
Evidence sources
Consumers
Validation source
```

Go deeper:
- [`03-analysis/ownership`](../../03-analysis/ownership/)
- [`04-knowledge-structure/canonical-ownership`](../../04-knowledge-structure/canonical-ownership/)
- [`05-collaboration/knowledge-contribution`](../../05-collaboration/knowledge-contribution/)
