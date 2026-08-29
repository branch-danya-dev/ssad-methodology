# 08 · Knowledge Update

[Русская версия](README.ru.md)

Knowledge Update closes the delivery loop by making the documentation reflect the **system that now actually exists**.

The stage is not “write documentation after development.”

> **Knowledge Update stabilizes validated system knowledge at its canonical owners after implementation and verification have produced evidence.**

## Main question

> Which claims about the system became true, false, incomplete or obsolete because of this change?

## Input

Knowledge Update uses:

- the verified target behavior;
- implementation evidence;
- resolved review and delivery feedback;
- final contracts and state behavior;
- actual data/migration outcomes;
- changed trust and failure semantics;
- confirmed system invariants;
- any decisions made during delivery;
- the Change Surface and affected canonical owners.

## What gets updated

Update stable system knowledge, not merely the task record.

Possible affected owners include:

```text
requirements / business rules
system boundaries
responsibility definitions
ownership
behavior and state models
data models
API / interface contracts
integration boundaries
flows
trust policy
failure behavior
system invariants
operational constraints
```

The physical files depend on the real system structure.

## From task knowledge to system knowledge

A delivery specification answers:

> What does this change need to implement?

Canonical system knowledge answers:

> How does the system work now?

After verification, stable facts should move into or update the second category.

```text
Change request
↓
Analysis
↓
Specification
↓
Implementation evidence
↓
Verification
↓
Stable system fact
↓
Canonical owner
```

The task remains useful historical context, but it should not become the only place where the current system can be understood.

## Selective update

Do not rewrite the entire knowledge base after every task.

Use affected ownership and Change Surface:

```text
Which claims were reopened?
Which of them changed?
Which dependent knowledge is now stale?
Which areas were checked and remain unchanged?
```

Only the relevant canonical knowledge needs stabilization.

This connects directly to [`../../06-change/selective-reopening/`](../../06-change/selective-reopening/).

## Canonical ownership rule

Suppose a specification introduced a new endpoint and changed an access rule.

After delivery:

```text
Task specification
→ retains delivery context

Backend API owner
→ receives the final HTTP contract

Access policy owner
→ receives the final access rule

System flow
→ updates if the end-to-end scenario changed
```

Do not leave the final truth only in the task because “the team already knows it.”

## Remove obsolete knowledge

Updating knowledge includes deletion and correction.

A stale document can be more harmful than a missing document because it looks authoritative.

Check for:

- replaced contracts;
- old diagrams;
- invalid assumptions;
- duplicated facts created during delivery;
- temporary migration notes presented as permanent rules;
- examples that no longer match canonical behavior.

> **Knowledge is stabilized not only by adding the new truth, but also by removing competing old truth.**

## Example · Aveli billing authority

Assume an early task description said:

```text
RevenueCat determines whether the user has access.
```

During analysis and implementation the model is corrected:

```text
RevenueCat
→ billing evidence

Aveli Backend
→ normalized billing state
→ final AccessStatus decision
```

After verification, it is not enough to update the implementation ticket.

The canonical integration, backend access model and relevant system flow must express the corrected ownership. Any old statement that gives RevenueCat product authority must be removed or rewritten.

## Implementation evidence vs permanent knowledge

Some implementation details should remain evidence rather than methodology-level truth.

Ask:

```text
Will this fact help someone understand behavior,
ownership, constraints or future change impact?
```

If yes, preserve it in the appropriate knowledge area.

If it is only incidental code detail with no analytical significance, the source code may remain the best owner.

## Completion check

Knowledge Update is complete when:

- all materially changed canonical claims are updated;
- obsolete competing claims are removed;
- final contracts and state semantics match implementation;
- cross-component flows and invariants still explain the real system;
- links point to the current canonical owners;
- temporary delivery context has not become accidental canonical truth;
- the next analyst or developer can understand the changed area without reconstructing it from closed tickets and chat;
- the repository once again represents one coherent current system model.

## Workflow closes — and can start again

```text
PRE-ANALYSIS
→ REQUIREMENTS
→ ANALYSIS & DESIGN
→ SPECIFICATION
→ REVIEW
→ GROOMING
→ DELIVERY SUPPORT
→ VERIFICATION
→ KNOWLEDGE UPDATE
        ↓
current system knowledge
        ↓
next change
```

Continue with the analytical toolkit: [`../../03-analysis/`](../../03-analysis/).
