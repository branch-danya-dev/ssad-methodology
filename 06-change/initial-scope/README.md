# Initial Scope

A change to an existing system should not begin with a proposed implementation.

It begins with:

> **What observable system behavior is expected to change?**

The initial scope separates the goal from the suggested solution and records:

```text
REQUEST
  ↓
EXPECTED BEHAVIOR CHANGE
  ↓
PRIMARY ACTORS / SCENARIOS
  ↓
KNOWN CONSTRAINTS
  ↓
INITIAL SCOPE
```

It is deliberately incomplete. It is a starting hypothesis that will later expand through dependencies, responsibility boundaries and ownership.

Useful questions:

- what becomes possible or impossible?
- for whom?
- in which scenario?
- what must remain unchanged?
- which external systems are already known to participate?
- which constraints and open questions exist?

A good initial scope contains the goal, observed behavior change, primary actors and scenario, known affected boundaries, must-not-change invariants, constraints and open questions.

The key rule is: **do not confuse the request with the real impact scope.**

Next: [`../change-surface/`](../change-surface/).
