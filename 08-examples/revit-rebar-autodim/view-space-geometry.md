# View-Space Geometry · context changes meaning

[Русская версия](view-space-geometry.ru.md)

## Problem

Rebar AutoDim dimensions geometry that already exists in the Revit model, but annotation meaning is not derived directly from global project X/Y axes.

For this system:

```text
model geometry
+
active view orientation
        ↓
annotation geometry meaning
```

The same structural geometry may be viewed under different orientations. Width, height, left, right, above, below and dimension placement must therefore be interpreted in the current view frame.

## Ownership distinction

Revit owns the source geometry.

The active view owns the contextual frame used for annotation interpretation.

Rebar AutoDim owns the normalized representation produced from those two inputs.

```text
Revit structural geometry
        ↓ evidence

Active view
→ Origin
→ RightDirection
→ UpDirection
→ ViewDirection
→ scale
        ↓ context

Rebar AutoDim Geometry
→ ZoneGeometry
```

No single one of those inputs alone owns the final annotation meaning.

## Normalized local model

The plugin projects source points into a view-local coordinate system:

```text
u → horizontal on the view
v → vertical on the view
w → depth relative to view plane
```

Then it builds a local model:

```text
ZoneGeometry
├── Left
├── Right
├── Bottom
├── Top
├── Width
├── Height
└── Center
```

This is a strong example of SSAD local modeling:

> **A local model may be canonical for one responsibility even when every underlying fact originates elsewhere.**

`ZoneGeometry` does not replace Revit geometry. It is the canonical interpretation owned by the plugin for its annotation responsibility.

## Evidence hierarchy

The preferred evidence is the actual reinforcement boundary.

A supported view-specific fallback may be used only when it preserves the required rectangular meaning.

```text
boundary evidence available?
        ↓ yes
normalize

        ↓ no
supported fallback reliable?
        ↓ yes             ↓ no
normalize               skip
```

The fallback does not grant permission to invent a rectangle merely because a dimension would be useful.

This connects directly to the SSAD principle:

```text
insufficient evidence
!= permission to manufacture certainty
```

## Context is part of change analysis

A source reinforcement zone may remain unchanged while the execution context changes.

Examples:

- a different active view;
- changed view orientation;
- changed scale;
- changed crop region;
- changed visibility.

That means the previous annotation interpretation may no longer be current even if the structural element itself did not change.

```text
source unchanged
+
context changed
        ↓
reopen geometry/layout interpretation
```

This is a useful Change Surface lesson: changes to context can reopen derived knowledge without changing the source entity.

## Why this matters for SSAD

Many systems contain meaning that is contextual rather than intrinsic:

```text
raw fact
+
interpretation context
→ system meaning
```

Rebar AutoDim demonstrates that SSAD ownership should not force all meaning into the source-data owner.

The correct questions are:

```text
Who owns the source fact?
Who owns the context?
Who owns the derived interpretation?
When must that interpretation be reopened?
```

## Methodological lesson

> **Canonical knowledge can be derived knowledge. What matters is explicit ownership of the interpretation and its validity conditions.**

Canonical project knowledge:
https://github.com/branch-danya-dev/revit-rebar-autodim-analysis/tree/main/geometry

Next: [`Semantic Reference`](semantic-reference.md)
