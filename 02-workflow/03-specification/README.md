# 03 · Specification

[Русская версия](README.ru.md)

Specification turns an agreed analytical solution into an **implementation-relevant view of the change**.

It does not replace the canonical system knowledge created during Requirements and Analysis & Design.

> **A specification is a delivery projection of system knowledge, not a new owner of every fact it references.**

## Main question

> What exactly should the team implement, and what observable system behavior should exist when the change is complete?

## Input

Specification starts from knowledge that is already sufficiently mature:

- problem and expected outcome;
- scope and non-goals;
- behavioral requirements;
- relevant design decisions;
- affected responsibility areas and owners;
- states and data implications;
- contracts and integrations;
- failure behavior;
- compatibility constraints;
- acceptance conditions;
- unresolved decisions that may still block delivery.

If a critical ownership, requirement or design question is still unknown, Specification must not hide it by converting the assumption into definitive wording. The work returns to the relevant earlier stage.

## What the system analyst does

The analyst selects the change-specific slice of system knowledge and makes it actionable for implementation and verification.

Typical work includes:

1. state the purpose and boundaries of the change;
2. describe current and target behavior when the distinction matters;
3. identify affected responsibilities and canonical owners;
4. stabilize behavioral rules, states and transitions;
5. describe data and contract changes;
6. make failure behavior explicit;
7. capture migration and compatibility requirements;
8. define observable acceptance criteria;
9. link canonical knowledge instead of copying it unnecessarily;
10. keep remaining assumptions and open questions visible.

## Working structure

A useful specification may contain:

```text
Purpose / Change
Scope / Non-goals
Current behavior
Target behavior
Affected responsibilities
Behavioral rules
States / transitions
Data changes
Contracts / interfaces
Failure behavior
Compatibility / migration
Acceptance criteria
Dependencies
Open questions / assumptions
Canonical knowledge links
```

This is not a mandatory document template. A small change may require only a compact change description and contract diff; a complex change may use several linked artifacts.

The responsibility is mandatory, not the physical shape of the document.

## Canonical knowledge vs delivery context

Suppose an API contract is canonically owned by the backend API documentation.

A task specification may say:

```text
The change adds POST /v1/billing/sync.

Canonical contract:
→ backend/api/billing-sync

For this delivery:
→ call occurs after a successful client-side purchase
→ result refreshes AccessStatus
→ timeout must not delete local workspace data
```

The specification provides enough context for the change without becoming a second independent owner of the API contract.

> **Duplicate context when it reduces reading cost. Do not duplicate canonical truth.**

## Traceability without bureaucracy

SSAD needs enough traceability to answer:

```text
Why is this being implemented?
Which system decision produced this behavior?
Which canonical knowledge does it affect?
How will the team verify it?
```

A lightweight chain is sufficient:

```text
Requirement
   ↓
Analysis / Design decision
   ↓
Specification
   ↓
Implementation / QA verification
```

Traceability should help reasoning and change impact, not create a second administrative system.

## Example · Aveli access synchronization

A weak specification might say:

```text
After purchase, enable premium access.
```

That wording hides ownership and system behavior.

A stronger delivery projection is:

```text
After a successful store purchase:
1. Frontend requests billing synchronization from the backend.
2. Backend reconciles provider billing evidence.
3. Backend computes the resulting AccessStatus.
4. Frontend consumes AccessStatus and opens the workspace only when access is allowed.
5. Provider failure does not directly grant access.
6. Loss of access verification does not delete professional workspace data.
```

The canonical billing, access and integration models remain with their respective owners. The specification only assembles the affected slice for delivery.

## Return conditions

Return to earlier stages when specification exposes:

- missing or contradictory requirement → [`01-requirements/`](../01-requirements/);
- undefined boundary, ownership, state or contract → [`02-analysis-and-design/`](../02-analysis-and-design/);
- unresolved decision that materially changes implementation → analysis and decision resolution before review.

## Completion check

Specification is ready for review when:

- purpose and scope are understandable without guessing;
- target behavior is explicit;
- affected responsibilities and owners are known;
- state/data/contract changes are described where relevant;
- failure and compatibility behavior are not implicit;
- critical assumptions are either resolved or clearly blocking;
- acceptance criteria are observable and testable;
- canonical knowledge is linked rather than silently duplicated;
- Dev and QA can reason about the same intended change.

Next: [`04-review/`](../04-review/)
