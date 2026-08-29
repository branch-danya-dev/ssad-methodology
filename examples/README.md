# Synthetic Examples

[Русская версия](README.ru.md)

This directory contains **fictional or deliberately simplified systems** used to explain SSAD.

Examples are teaching and exploration artifacts. They do not claim that the described product, codebase, infrastructure, or implementation exists.

## Why Synthetic Examples Exist

A methodology needs to demonstrate behavior across different system shapes without requiring a complete real project for every question.

An example may therefore be intentionally designed to show:

- a system with no backend;
- a host-application boundary;
- distributed data ownership;
- asynchronous communication;
- an external authority;
- an operations perspective;
- a boundary-changing feature;
- a difficult Change Surface.

## Rules for Examples

Every example SHOULD state:

```text
purpose
system shape
assumptions
analytical perspectives
ownership model
what SSAD principle it demonstrates
which details are intentionally simplified
```

An example MUST NOT be presented as implementation evidence.

## Current Examples

| Example | Shape | Focus |
|---|---|---|
| [Mobile Application](mobile-application/) | client + backend + local/server persistence | data ownership and synchronization |
| [Desktop Plugin](desktop-plugin/) | plugin + host application + filesystem | host boundary and non-product-shaped perspectives |
| [Event-Driven Platform](event-driven-platform/) | services + messaging + data + operations | distributed ownership and asynchronous contracts |

These examples are intentionally different from one another. Their purpose is to demonstrate that SSAD follows the system rather than one universal repository tree.
