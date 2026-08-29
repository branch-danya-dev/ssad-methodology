# Knowledge Feedback Loop

Implementation, testing and operations are sources of new evidence, so system knowledge does not stop evolving after specification or grooming.

```text
Analysis
→ Specification
→ Implementation
→ Observed evidence
→ Model check
→ Knowledge update
```

New evidence may expose unsupported assumptions, hidden storage constraints, different integration behavior, ambiguous transitions or new failure modes.

A practical loop is:

```text
new evidence
→ compare with current model
→ identify canonical owner
→ model wrong or implementation wrong?
→ reopen analysis or fix implementation
→ verify again
→ update canonical knowledge
```

Not every implementation detail changes system knowledge. The analyst first determines the impact surface: contract, state semantics, ownership, trust, failures or only local implementation detail.

Operations and Support are also part of this loop because production logs, incidents, user reports and integration failures provide system evidence.

> If implementation changes our understanding of the system, the knowledge work is not finished.
