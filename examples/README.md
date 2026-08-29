# Synthetic Examples

[Русская версия](README.ru.md)

This directory contains **fictional or deliberately simplified systems** used to explain SSAD.

Examples do not claim that the described product, codebase, infrastructure, or implementation exists.

## Example Depth

SSAD examples may be:

```text
focused
→ illustrates one or two methodology ideas

worked
→ follows a substantial part of the workflow
→ shows both construction and stable knowledge ownership
→ may include a change-analysis walkthrough
```

## Current Examples

| Example | Shape | Focus | Depth |
|---|---|---|---|
| [Mobile Application](mobile-application/) | client + backend + local/server persistence | data ownership and synchronization | focused |
| [Desktop Plugin](desktop-plugin/) | plugin + host application + filesystem | workflow → baseline → change | **worked** |
| [Event-Driven Platform](event-driven-platform/) | services + messaging + data + operations | distributed ownership and asynchronous contracts | focused |

## Recommended Worked Example

Start with [`desktop-plugin/`](desktop-plugin/).

It deliberately separates:

```text
walkthrough/
→ temporal analysis process

baseline/
→ stable system-shaped knowledge

changes/
→ evolution after stabilization
```

This layout belongs to the **teaching example**, not to the analyzed system itself.

The stable documentation inside `baseline/` is organized by actual owners:

```text
business/
plugin/
host-application/
filesystem/
system/
```

That difference is intentional and central to SSAD.

## Rules for Examples

Every example SHOULD state its purpose, assumptions, system shape, analytical perspectives, ownership model, demonstrated SSAD principle, and intentional simplifications.

An example MUST NOT be presented as real implementation evidence.
