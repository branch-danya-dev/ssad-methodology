# Validation

Validation checks system knowledge through participants who can expose different classes of error.

> The goal is not formal approval. The goal is to discover wrong assumptions before implementation.

Different perspectives validate different things:

- Business → problem and expected behavior;
- Architecture → boundaries and dependencies;
- Development → feasibility and implementation constraints;
- QA → ambiguity, edge cases and testability;
- Integration Owner → external contract semantics;
- Security / Operations → trust, failure and operational constraints.

Validation applies to boundaries, ownership, behavior, states, data, interfaces, integrations, failures, trust assumptions, acceptance criteria and end-to-end flows.

A practical sequence is:

```text
claim/model
→ possible error class
→ appropriate validator
→ focused context
→ confirmed / changed / rejected / open
→ canonical knowledge update
```

Review is one workflow mechanism for validation, but validation also happens during requirements, design, grooming, implementation, QA and production evidence.

> **SSAD validates claims about the system, not documents as text.**
