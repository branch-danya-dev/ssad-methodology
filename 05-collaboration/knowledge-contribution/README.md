# Knowledge Contribution

SSAD treats the team not as passive documentation consumers but as a **distributed source of system knowledge**.

The key question is:

> What knowledge can this participant confirm, reject, constrain or enrich?

Roles are not enough. Before an interaction, define the claim being checked, whether it is a fact, decision or constraint, who owns it, who can provide evidence, and what counts as sufficient confirmation.

Typical contributions include:

- Client / Requester → original problem and expected outcome;
- Product / Business → business rules and priorities;
- Architect → architectural constraints and allowed dependencies;
- Developer → implementation evidence and feasibility;
- QA → ambiguity, edge cases and testability;
- Integration Owner → external contracts and actual integration behavior;
- Security → trust boundaries and protection constraints;
- Operations / Support → operational evidence and real failure modes.

A critical distinction is **evidence vs authority**. Someone may know how the system works today without owning the decision about how it should work.

Useful collaboration changes knowledge state:

```text
UNKNOWN
→ HYPOTHESIS
→ CONFIRMED / REJECTED / CONFLICTED
```

If new evidence changes a canonical model, it must flow back to that model's owner.
