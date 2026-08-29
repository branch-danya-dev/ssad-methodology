# Integration checklist

[Русская версия](README.ru.md)

Use this when analyzing a new or changed integration.

Check:
- external ownership boundary;
- purpose and trigger;
- contract semantics;
- data and decision ownership;
- evidence versus authority;
- sync/async behavior;
- timeout, retry, idempotency and deduplication;
- degraded behavior and recovery;
- trust and validity assumptions;
- reconciliation rules.

Minimum output:

```text
Integration purpose
Ownership boundary
Contract semantics
Data / decision ownership
Trigger and flow position
Retry / idempotency rules
Failure behavior
Trust assumptions
Reconciliation rules
Open questions
```

Go deeper:
- [`03-analysis/integrations`](../../03-analysis/integrations/)
- [`03-analysis/interfaces`](../../03-analysis/interfaces/)
- [`03-analysis/trust`](../../03-analysis/trust/)
- [`03-analysis/failures`](../../03-analysis/failures/)
