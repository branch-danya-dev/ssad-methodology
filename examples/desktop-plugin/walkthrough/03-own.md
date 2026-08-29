# 03 — OWN

[Русская версия](03-own.ru.md)

## Question

Who owns each important decision and state?

## Ownership Table

| Knowledge / State | Canonical owner | Consumers |
|---|---|---|
| selected sheets in open document | Host Application | Plugin |
| source document identity | Host Application | Plugin, Manifest |
| sheet identity and name | Host Application | Plugin, Manifest |
| export orchestration | Plugin | User |
| per-sheet export status | Plugin | Manifest, User |
| physical PDF persistence | Filesystem | User, Plugin |
| manifest content | Plugin | User / later automation |
| manifest file persistence | Filesystem | User |
| source document mutation policy | Business | Plugin, verification |
| cross-component export invariant | System | all perspectives |

## Important Distinctions

### Host state is not plugin state

The plugin may hold a temporary snapshot of selected sheet IDs, but that does not make the plugin the canonical owner of sheet identity.

### Filesystem persistence is not export meaning

The filesystem can persist bytes, but it does not decide whether the export job is considered successful.

### Plugin result is not host result

The host reports the outcome of an individual export operation. The plugin interprets multiple outcomes into one user-visible job result.

## Resolved Unknown

For this example we decide:

`OPEN-04 → DECIDED`

The manifest contains:

```text
sourceDocumentId
exportedAt
outputDirectory
items[]
  sheetId
  sheetName
  fileName
  status
  errorCode?
```

This is a **scenario decision**, not real implementation evidence.

## Gate

No important state has two competing canonical owners.

Next: [`04-model.md`](04-model.md)
