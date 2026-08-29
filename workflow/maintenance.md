# Knowledge Maintenance Workflow

[Русская версия](maintenance.ru.md)

SSAD treats documentation as a maintained system model.

## Triggers

Maintenance may be triggered by implementation changes, product decisions, API/schema changes, provider/platform changes, incidents, security changes, architecture decisions, discovered contradictions, or outdated evidence.

## Workflow

```text
Change detected
→ find canonical owner
→ determine Change Surface
→ update canonical knowledge
→ update contextual references
→ update traceability
→ verify diagrams/contracts/examples
→ classify remaining unknowns
→ restore Stable status
```

## Legacy Refactoring

Before deleting or restructuring documentation:

1. establish the new canonical owner;
2. inspect old documentation for unique/orphan knowledge;
3. migrate unique knowledge;
4. fix references;
5. remove duplicates;
6. rerun consistency review.

Never delete documentation solely because a newer directory exists.

## Drift Detection

Useful checks include dead links, bilingual mismatch, undocumented components, technology without owner, duplicated contracts, diagram/prose disagreement, schema/document mismatch, and hidden `OPEN` items.
