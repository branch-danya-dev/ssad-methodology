# 08 · Examples

[Русская версия](README.ru.md)

This section shows **what SSAD looks like in practice and whether it survives contact with a real system**.

Examples are not a showcase and not a collection of templates to copy.

Their purpose is to demonstrate that the principles from the previous sections combine into one workable analysis model.

## Two kinds of examples

```text
Synthetic
→ inexpensive exploration of one focused idea

Real-world
→ validation against an actual system,
  real constraints and real ownership
```

Synthetic examples are useful for teaching an isolated concept.

The methodology itself should be validated by real-world cases.

## Primary real-world case: Aveli

Full repository:

https://github.com/branch-danya-dev/aveli-system-analysis

Aveli is not used because its folder tree is a “correct SSAD template.”

It demonstrates the opposite: the knowledge structure emerged from this system's actual responsibility areas.

```text
business/
database/
backend/
frontend/
integrations/
system/
```

## Learning route

[`aveli/`](aveli/) contains three connected slices:

```text
1. Repository Structure
   ↓
how responsibility boundaries become knowledge structure

2. Access Ownership
   ↓
how evidence, ownership, integration and flow are separated

3. Offline Trust
   ↓
how trust, states, failures and invariants combine into system behavior
```

Together they form one end-to-end path:

```text
SYSTEM STRUCTURE
↓
CANONICAL OWNERSHIP
↓
CROSS-BOUNDARY FLOW
↓
TRUST & FAILURE POLICY
↓
SYSTEM SYNTHESIS
```

## Main rule for examples

An example may:

- simplify context;
- isolate one analytical question;
- show a diagram;
- explain the reasoning path.

But it must not become a second canonical version of project knowledge.

> **Theory is explained through an example. Project truth remains with its canonical owner.**

Each Aveli slice therefore links back to the full repository and the relevant SSAD chapters.

## Start

→ [`Aveli · end-to-end example`](aveli/README.md)

Back to: [`README.md`](../README.md)
