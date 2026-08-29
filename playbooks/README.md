# SSAD Playbooks

[Русская версия](README.ru.md)

Playbooks translate SSAD from methodology into **repeatable analyst work**.

They answer:

> **Given my current situation, what should I do next?**

A playbook does not define the final repository tree. It defines a practical sequence of questions, checks, outputs, and gates.

## Core Playbooks

| Starting condition | Playbook |
|---|---|
| the system or subsystem is new | [`new-system.md`](new-system.md) |
| the system exists but knowledge is unreliable or fragmented | [`existing-system.md`](existing-system.md) |
| a trusted baseline exists and a material change arrives | [`change.md`](change.md) |

Quick chooser: [`quick-reference.md`](quick-reference.md)

## Shared Playbook Shape

Each playbook follows the same structure:

```text
Use When
Inputs
Steps
Expected Outputs
Quality Gates
Stop / Reopen Conditions
Common Failure Modes
Exit Criteria
```

## Playbooks vs Workflow

The canonical workflow is:

```text
DISCOVER → BOUND → OWN → MODEL → CONNECT → SYNTHESIZE → VERIFY → STABILIZE → EVOLVE
```

Playbooks do not replace it.

Instead, each playbook **selects and emphasizes the parts of the workflow appropriate to the starting condition**.

Example:

```text
New system
→ heavy BOUND + OWN work

Existing system
→ heavy DISCOVER + evidence reconciliation

Change
→ heavy Change Surface + targeted reopening
```

## Branches, Not Separate Methodologies

The following are currently treated as branches of the three core playbooks:

```text
integration change
architecture change
technology replacement
legacy documentation migration
data migration
provider change
security / regulatory change
```

They may become separate playbooks later if repeated applications show that they require materially different work.

## Rule

> **Do not create a new playbook because a task has a different name. Create one only when the dependency structure of the work is materially different.**
