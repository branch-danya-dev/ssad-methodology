# 07 — VERIFY

[Русская версия](07-verify.ru.md)

## Question

Do the perspectives agree with each other and with the declared scenario evidence?

## Verification Matrix

| Check | Result |
|---|---|
| `E-08` source document unchanged ↔ `BR-01` | PASS |
| `BR-02` independent attempts ↔ plugin state | PASS |
| plugin manifest ownership ↔ filesystem persistence | PASS |
| per-sheet statuses ↔ system whole-job result | PASS |
| baseline has no network dependency ↔ repository perspectives | PASS |
| system invariants ↔ owner-local behavior | PASS |

## Contradiction Found

During verification, `OPEN-01` becomes important:

> What happens if the target PDF already exists?

Without a collision policy, the filesystem behavior can contradict `BR-03`.

Example:

```text
existing A101.pdf
+
new A101 export fails after truncating/replacing file
=
previous successful user data may be lost
```

## Reopen Upstream Knowledge

The issue returns to business behavior and filesystem expectations.

Scenario decision:

`OPEN-01 → DECIDED`

```text
Existing output files are never overwritten silently.

For each collision the plugin must either:
1. obtain explicit overwrite approval before export; or
2. choose a non-conflicting target name.

A failed export must not destroy a pre-existing file.
```

This produces:

`BR-05` — Existing output files must not be destructively overwritten without explicit user approval.

And:

`SI-06` — An export failure must not reduce the set of valid pre-existing output files.

## Why This Matters

The walkthrough is intentionally not a clean one-pass chain.

`VERIFY` discovered a missing upstream rule and reopened earlier knowledge.

That is expected SSAD behavior.

## Gate

After the collision policy is added, no material contradiction remains in the conceptual baseline.

Next: [`08-stabilize.md`](08-stabilize.md)
