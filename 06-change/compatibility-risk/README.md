# Compatibility & Risk

Change Surface asks what may be affected.

Compatibility & Risk asks:

> **Which existing expectations, contracts and invariants may stop being true after the change?**

Inspect at least:

```text
Behavior compatibility
State compatibility
Data compatibility
Contract compatibility
Integration compatibility
Operational compatibility
Trust compatibility
```

For contracts, check old/new producer-consumer combinations, required fields, semantic changes, event ordering and versioning.

For data, check existing records, migrations, mixed-version periods and rollback.

For states, check legacy states, new transitions and rollback behavior.

A lightweight risk model is often enough:

```text
Likelihood
Impact
Detectability
Recoverability
```

Recoverability matters because equally likely failures can have very different consequences.

The output should make rollout, migration, rollback or forward-fix strategy, critical invariants and mitigations explicit.

Next: [`../selective-reopening/`](../selective-reopening/).
