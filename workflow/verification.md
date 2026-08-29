# Verification and Quality Gates

[Русская версия](verification.ru.md)

Quality gates are **readiness checks**, not organizational ceremonies.

## Gate 1 — Scope Ready
- problem and scope are understandable;
- in/out of scope is explicit;
- actors and external systems are known;
- important unknowns are visible.

## Gate 2 — Ownership Ready
- major responsibilities have owners;
- canonical state owners are known;
- consumers are separated from owners;
- competing sources of truth are resolved or explicitly reconciled.

## Gate 3 — Data Ready
- data ownership is explicit;
- conceptual/logical models preserve real boundaries;
- physical persistence owners are clear;
- lifecycle/migration constraints are represented where needed.

## Gate 4 — Component Ready
- responsibilities are explicit;
- behavior is not duplicated across owners;
- interfaces link to owners;
- technology usage follows responsibility.

## Gate 5 — Integration Ready
- internal interfaces are separated from external integrations;
- external authority is explicit;
- exchanged data and trust are known;
- failure/retry/reconciliation is documented where material.

## Gate 6 — System Synthesis Ready
- cross-component flows agree with component knowledge;
- trust/authority is coherent;
- invariants do not contradict local behavior;
- system views link to canonical owners.

## Gate 7 — Stable Repository
- important requirements are traceable;
- acceptance/verification exists where required;
- links resolve;
- diagrams do not contradict prose;
- known uncertainty is explicit;
- no competing canonical definitions remain.

## Verification Matrix

```text
business rule      ↔ requirement
requirement        ↔ acceptance
requirement        ↔ component
API producer       ↔ API consumer
logical model      ↔ physical model
data owner         ↔ data consumer
technology claim   ↔ real usage
diagram            ↔ canonical prose
current-state doc  ↔ implementation evidence
system synthesis   ↔ component owners
```
