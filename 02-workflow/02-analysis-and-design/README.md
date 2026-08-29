# 02 · Analysis & Design

[Русская версия](README.ru.md)

This stage answers:

> **How do we turn requirements and constraints into a coherent system model and design?**

Requirements describe **what must be achieved**. Analysis & Design determines **which parts of the system are responsible, how they interact, and which knowledge must be aligned before implementation**.

## Inputs

Typical inputs:

- problem and goal;
- scope;
- requirements;
- constraints;
- known system participants;
- affected components and integrations;
- open questions;
- evidence / confidence status.

If critical requirements conflict or major constraints are unknown, this stage may reopen Requirements.

## Core SSAD logic

System design does not start from technologies or a predefined artifact list.

```text
BOUNDARIES
    ↓
RESPONSIBILITIES
    ↓
OWNERSHIP
    ↓
BEHAVIOR / STATES / DATA
    ↓
INTERFACES
    ↓
FLOWS
    ↓
SYSTEM SYNTHESIS
```

This is iterative, not waterfall.

## 1. Define boundaries

Clarify what belongs to the analyzed system, what is external, which actors and systems participate, and which parts of the request are internal changes versus external dependencies.

## 2. Split responsibilities

For each meaningful area ask:

- what behavior does it own;
- which decisions does it make;
- which data does it store;
- which interfaces does it provide;
- what does it depend on;
- what is explicitly outside its responsibility.

SSAD does not require fixed component names. One system may have `frontend`, `backend`, `database`; another may have `plugin`, `host`, `worker`, `gateway` or `operations`.

## 3. Define ownership

For each important piece of knowledge or state determine:

```text
Who makes the decision?
Who stores canonical state?
Who may mutate it?
Who consumes it?
Who verifies correctness?
```

Ownership should be clear before dependent contracts and behavior are stabilized.

## 4. Model behavior, states and data

### Behavior
- actions;
- conditions;
- rules;
- failure behavior.

### States
- valid states;
- transitions;
- invalid or terminal states;
- transition authority.

### Data
- entities;
- canonical state;
- copies and caches;
- mutation and propagation.

## 5. Define interfaces

For each boundary describe:

```text
Provider
Consumer
Contract owner
Input
Output
Errors
Versioning / compatibility
Failure behavior
```

A contract connects responsibility owners; it is not an isolated artifact.

## 6. Build end-to-end flows

Local models are insufficient if the whole-system behavior remains unclear.

```text
Actor
  ↓
Entry point
  ↓
Component A
  ↓
Contract
  ↓
Component B
  ↓
Data / external system
  ↓
Result
```

Failure flows should be modeled as well.

## 7. Perform system synthesis

Combine local knowledge into:

- system context;
- critical flows;
- trust / authority map;
- system invariants;
- cross-component failures;
- data movement;
- critical dependencies.

This verifies that locally correct decisions still form one coherent system.

## Team interaction

Analysis & Design is collaborative.

| Participant | What they validate |
|---|---|
| Product / BA | required behavior |
| Developers | feasibility and implementation evidence |
| QA | verifiability, edge and negative cases |
| Architect | boundaries and dependencies |
| Integration owner | contracts and external constraints |
| Security / Ops | trust, failures and operational constraints |

The team does not only receive the design; it feeds evidence back into it.

## Aveli example: subscription purchase

A naive view:

```text
User buys subscription
→ access granted
```

System analysis reveals:

```text
User
  ↓
App Store / Google Play
  ↓
RevenueCat
  ↓
Aveli Backend
  ↓
Access resolution
  ↓
Frontend
```

Ownership:

```text
Store
→ purchase fact

RevenueCat
→ normalized billing evidence

Backend
→ final access decision

Frontend
→ AccessStatus consumer
```

```mermaid
flowchart LR
    U[User] --> Store[App Store / Google Play]
    Store --> RC[RevenueCat]
    RC --> BE[Aveli Backend]
    BE --> AR[Access resolution]
    AR --> FE[Frontend]
```

The key conclusion is that a purchase should not directly mutate access in the frontend. Access is a separate system decision owned by the backend.

## Expected output

Useful output normally covers:

```text
System boundary
Responsibility areas
Ownership
Behavior
States
Data
Interfaces
Integrations
End-to-end flows
Failure behavior
Trust / authority
System invariants
Open decisions
```

SSAD does not require these to live in one file or in a predefined folder tree. Physical structure follows real knowledge ownership.

## Common mistakes

- starting from technology;
- designing APIs before ownership;
- describing components in isolation;
- ignoring failure behavior;
- treating a diagram as the complete system model.

## Completion check

This stage is ready to move forward when boundaries, responsibilities, ownership, core behavior, states, data, interfaces, end-to-end flows and failure behavior are coherent enough that the system can be explained as a whole and reviewed with dependency owners.

Next: `03-specification`.

Detailed analysis methods are developed in [`../../03-analysis/`](../../03-analysis/).
