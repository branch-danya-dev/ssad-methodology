# Semantic Reference · meaning before API representation

[Русская версия](semantic-reference.ru.md)

## Problem

Revit dimensions require technical `Reference` objects accepted by the host API.

But the analytical question comes first:

> **What structural fact should this dimension communicate?**

If the project starts from API objects instead, a technically convenient reference may silently redefine the intended system meaning.

## Two layers

```text
SEMANTIC TARGET
what should be dimensioned?

        ↓ realization

REVIT REFERENCE
how can that target be represented to NewDimension?
```

Examples of semantic targets:

- left/right boundaries of the normalized reinforcement zone;
- nearest valid structural grid on the left;
- nearest valid grid on the right;
- nearest valid grid above/below.

A Revit `Reference` is only a host-compatible representation of one of those targets.

## Direction before distance

Grid selection demonstrates why semantic rules must exist independently from API representation.

```text
          Above
            ↑
            │
Left ← [ Zone ] → Right
            │
            ↓
          Below
```

For a left-grid dimension, only grids on the left are eligible.

```text
closer grid on wrong side
!= valid semantic target
```

The host API may be perfectly capable of dimensioning to the wrong grid. That does not make the result correct.

## Supporting geometry as adaptation

Raw `Area Reinforcement` boundaries do not always expose stable references that Revit dimension creation can use.

The plugin may therefore create supporting detail geometry:

```text
canonical zone boundary intent
        ↓
Revit representation limitation
        ↓
supporting detail curve
        ↓
usable Reference
        ↓
native Dimension
```

The detail curve is not a new source of geometric truth.

It is an **adapter between system meaning and host representation**.

This distinction is important because implementation workarounds tend to become accidental architecture if their role is not explicit.

## Optionality vs failure

The SSAD migration also exposed two conditions that looked identical in a simple “dimension created / not created” model.

### No semantic target exists

Example: there is no structural grid on the right side.

```text
right grid target
→ NOT APPLICABLE
→ no right-grid dimension intended
```

### Semantic target exists but realization fails

Example: a valid grid/boundary target exists but Revit rejects the reference combination.

```text
semantic target exists
+
valid dimension intent exists
+
host realization fails
        ↓
FAILED WRITE / REFERENCE REALIZATION
```

These outcomes must not be collapsed.

```text
NOT REQUIRED
!=
FAILED TO REALIZE
```

The first is correct system behavior. The second is failure evidence.

## Ownership model

```text
Geometry
→ owns zone boundaries

References
→ owns semantic reference selection

Layout
→ owns dimension intent and placement

Revit Boundary
→ owns host-valid realization constraints

Annotations
→ owns the generated native result
```

No one responsibility needs to own every step.

The connection between owners is the system model.

## General SSAD lesson

The same pattern appears far beyond Revit:

```text
business/system meaning
!=
wire representation
!=
database representation
!=
framework object
```

OpenAPI DTOs, SQL rows, Kafka messages, SDK objects and Revit `Reference` values can all represent system meaning without owning it.

> **Choose the semantic target first. Then choose a technical representation that preserves it.**

Canonical project knowledge:
https://github.com/branch-danya-dev/revit-rebar-autodim-analysis/tree/main/references

Next: [`Generated Output Ownership`](generated-output-ownership.md)
