# System Construction Workflow

[Русская версия](construction.ru.md)

## DISCOVER — What do we actually know?

Inputs may include stakeholder knowledge, current behavior, source code, API/schema/configuration artifacts, existing documentation, constraints, and provider/platform contracts.

Output:

```text
evidence inventory
initial unknowns
initial vocabulary
```

## BOUND — What system are we analyzing?

Define scope, out of scope, actors, external systems, constraints, and the preliminary system boundary.

## OWN — Who owns important responsibility and state?

Determine:

```text
decision owner
state owner
change authority
consumer
verifier
```

No material state should have competing sources of truth without explicit reconciliation.

## MODEL — What behavior and structure must be represented?

Applicable models may include business rules, requirements, processes, data, states, API/contracts, components, trust/security, and technology usage.

Model only after relevant ownership is sufficiently understood.

## CONNECT — How do local pieces form dependencies?

Create requirement-to-component traces, owner-to-consumer links, technology-to-usage links, interface relationships, and cross-references.

## SYNTHESIZE — What belongs to the whole system?

Build system context, component relationships, end-to-end flows, authority/trust maps, cross-component data movement, invariants, and boundary-changing evolution.

## VERIFY

Cross-check:

```text
business ↔ technical behavior
logical ↔ physical data
producer ↔ consumer contracts
diagram ↔ prose
documentation ↔ evidence
requirement ↔ acceptance
technology ↔ real usage
```

## STABILIZE

```text
Draft → Baseline → Stable
```

A downstream finding may reopen any earlier stage. Iteration is expected; uncontrolled contradiction is not.
