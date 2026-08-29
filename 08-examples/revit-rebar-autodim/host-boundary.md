# Host Boundary · Revit authority vs plugin responsibility

[Русская версия](host-boundary.ru.md)

## Problem

Rebar AutoDim runs **inside Autodesk Revit**. That makes the system boundary unusual.

The plugin does not own the document, the view, structural geometry, native references or transaction engine. Yet it must make its own system decisions about how those facts are interpreted for reinforcement annotation.

If these concerns are collapsed, host API behavior starts to look like the business/system model.

## Boundary

```text
AUTODESK REVIT
owns
- document and view state
- Area Reinforcement source geometry
- structural grid geometry/references
- native element validity
- transaction semantics

             boundary
                ↓

REBAR AUTODIM
owns
- supported execution interpretation
- normalized zone meaning
- dimension/reference intent
- placement policy
- generated annotation result
- regeneration ownership
```

The plugin consumes Revit evidence and capabilities. It does not inherit ownership of the facts it reads.

## Read and write asymmetry

The plugin reads structural truth but writes only its own annotation layer.

```text
SOURCE MODEL
Area Reinforcement
Structural Grids
View Context
      ↓ read

REBAR AUTODIM
      ↓ write

PLUGIN-OWNED OUTPUT
Detail Curves
Dimensions
Generation Metadata
```

This is a stronger boundary than simply “uses Revit API”.

The invariant is:

> **An annotation convenience must not become permission to change structural source truth.**

## Host authority does not imply decision ownership

Revit decides whether a particular `Reference`, line, element creation or transaction is technically valid.

Rebar AutoDim decides whether that technical object represents the intended annotation meaning.

```text
Revit says:
“This Reference is valid for NewDimension.”

Rebar AutoDim still must answer:
“Is this the correct structural target for the intended dimension?”
```

A technically valid API call can still realize the wrong system meaning.

## Transaction boundary as system boundary

The historical implementation used a transaction for each supported reinforcement zone.

SSAD gives this implementation choice a system explanation:

```text
one source zone
→ one independently meaningful annotation result
→ one regeneration ownership relation
→ one atomic write scope
```

Therefore a failed zone can roll back without invalidating other already committed zones when Revit permits safe isolation.

```text
Zone A → commit
Zone B → rollback
Zone C → commit
```

The transaction is not merely a Revit programming detail. Its scope expresses the chosen failure-isolation boundary.

## What SSAD adds

Without explicit boundary analysis, this system could easily be documented as:

```text
Revit API
→ collect elements
→ calculate
→ call NewDimension
→ transaction commit
```

SSAD instead asks:

```text
What does Revit own?
What does the plugin own?
What evidence crosses the boundary?
Which decisions remain local to the plugin?
What failure scope is independently meaningful?
```

## Methodological lesson

An external dependency does not need to be a remote service to be an integration/authority boundary.

A host application may be closer and more authoritative than any HTTP provider while still remaining outside the plugin's responsibility area.

> **Physical co-location does not eliminate ownership boundaries.**

Canonical project knowledge:
https://github.com/branch-danya-dev/revit-rebar-autodim-analysis/tree/main/revit-boundary

Next: [`View-Space Geometry`](view-space-geometry.md)
