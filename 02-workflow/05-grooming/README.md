# 05 · Grooming

[Русская версия](README.ru.md)

Grooming synchronizes the team around a reviewed solution before implementation begins.

Review and Grooming answer different questions:

```text
Review
→ Is the solution correct?

Grooming
→ Does the team understand the change in the same way and have enough knowledge to implement it?
```

> **Grooming is a readiness and shared-understanding check, not a ritual reading of the specification.**

## Main question

> Can the implementation team start work without relying on materially different assumptions about behavior, scope, ownership or acceptance?

## Input

Grooming starts from a review-ready or reviewed change description:

- problem and expected result;
- scope and non-goals;
- target behavior;
- affected responsibilities;
- relevant states, data and contracts;
- dependencies and integration constraints;
- failure and compatibility behavior;
- acceptance criteria;
- known risks and unresolved non-blocking questions.

If fundamental requirements or design are still unstable, grooming should expose that and return the work upstream rather than force a delivery estimate.

## What happens during grooming

The team should align on:

1. why the change exists;
2. what observable behavior is expected;
3. which system areas are affected;
4. which parts explicitly remain out of scope;
5. which rules, states and transitions are easy to misinterpret;
6. which contracts or external dependencies matter;
7. which negative and edge scenarios must be handled;
8. what QA will verify;
9. how the implementation may be split without losing system meaning;
10. which questions remain and whether they block work.

## Questions worth asking

### Behavior

- What exactly changes for the user or another system?
- Which current behavior must remain unchanged?
- What happens in negative scenarios?

### Boundaries and ownership

- Which components or responsibility areas will change?
- Who owns each relevant decision or contract?
- Are any dependencies being treated as if they were internal when they are not?

### Data and states

- Does the change introduce a new state or transition?
- Which component is allowed to perform that transition?
- Are there migration, cache or persistence implications?

### Interfaces and integrations

- Which contract changes?
- Is the change backward compatible?
- What happens on timeout, duplicate request, retry or partial failure?

### Verification

- Can QA derive concrete scenarios from the agreed behavior?
- What result would prove that the change is implemented correctly?

## Grooming as a feedback loop

Grooming may reveal missing knowledge even after review.

```text
Reviewed specification
↓
Grooming
├─ answer exists in canonical knowledge → clarify and continue
├─ new fact → Analysis & Design
├─ missing requirement → Requirements
├─ unclear wording → Specification
├─ unresolved ownership/decision → Collaboration / decision resolution
└─ shared understanding reached → Delivery Support
```

That is not a failed grooming session. It is the team finding an inconsistency before code makes it more expensive.

## Task decomposition

Task splitting should follow understanding, not replace it.

Weak sequence:

```text
Open ticket
→ immediately split frontend/backend tasks
→ discover later that ownership and behavior were unclear
```

Better sequence:

```text
Understand end-to-end behavior
↓
Identify affected responsibilities
↓
Understand dependencies and contracts
↓
Split implementation work
```

A technical task may be local while its reason and acceptance remain cross-system.

## Example · Aveli billing change

Suppose the reviewed change introduces a new billing synchronization endpoint.

During grooming the team should be able to explain together:

```text
Frontend
→ triggers synchronization after purchase

Backend
→ reconciles provider evidence
→ computes AccessStatus

RevenueCat
→ external billing evidence source

QA
→ verifies success, provider failure, duplicate sync,
  stale access state and offline behavior
```

If one developer assumes RevenueCat directly grants access while another assumes the backend owns access authority, the change is not ready even if the ticket is estimated.

## Completion check

Grooming is complete when:

- the team can explain the target behavior consistently;
- scope and non-goals are understood;
- affected responsibilities and dependencies are known;
- important states, contracts and failure paths are understood;
- blocking questions are resolved;
- acceptance criteria are clear enough for implementation and QA;
- task decomposition preserves the system model;
- no participant must invent a critical product or system rule during coding.

> **Ready means shared understanding is sufficient for implementation — not that every possible detail is known in advance.**

Next: [`06-delivery-support/`](../06-delivery-support/)
