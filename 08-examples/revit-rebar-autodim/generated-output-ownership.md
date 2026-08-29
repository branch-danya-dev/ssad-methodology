# Generated Output Ownership · source state vs derived state

[Русская версия](generated-output-ownership.ru.md)

## Problem

Rebar AutoDim does not own the reinforcement design it reads from Revit.

But it does own something important: the annotation result that it generated from that source.

Without an explicit ownership model, repeated execution easily degenerates into duplicate accumulation or ambiguous partial manual state.

## Two different state owners

```text
STRUCTURAL SOURCE STATE
Area Reinforcement
Structural Grids
        ↓ owned by Revit / structural model

DERIVED PLUGIN STATE
GeneratedAnnotationSet
Generation Metadata
        ↓ owned by Rebar AutoDim
```

The generated state communicates source facts, but it is not the source state itself.

This allows the plugin to replace its own output without claiming authority over reinforcement design.

## One current result per source zone

The useful ownership relation is:

```text
Area Reinforcement identity
        ↓
Generation Metadata
        ↓
Current Generated Annotation Result
```

For the current plugin model, one source zone should converge to one current plugin-owned annotation result.

The result may contain:

- supporting detail curves;
- required overall width and height dimensions;
- conditional grid-offset dimensions;
- generation identity/metadata.

## Regeneration instead of patch synchronization

On rerun, the plugin does not attempt to preserve and individually patch every generated dimension.

```text
find previous plugin-owned result
        ↓
remove previous result
        ↓
read current source/context
        ↓
recalculate
        ↓
create one new complete result
        ↓
store current ownership metadata
```

This gives idempotency a semantic meaning:

```text
unchanged source + unchanged context
Run 1 → Result A
Run 2 → replace A → Result A'

A' ≈ A in system meaning
```

Stable element IDs are not required. Stable meaning is.

## Manual edits and ownership ambiguity

A user may manually delete or partially modify plugin-generated elements.

The plugin does not treat those partial edits as a new canonical hybrid model.

```text
partial plugin-owned result
        ↓
next run
        ↓
remove remaining owned output
        ↓
regenerate from current source truth
```

This is an ownership decision:

> **If an element remains inside the plugin-owned generated set, the plugin is allowed to replace it.**

If the product wanted durable user edits inside generated output, ownership rules would need to change rather than merely adding patch logic.

## Atomic replacement

The unsafe outcome is:

```text
old result partially deleted
+
new result partially created
```

The desired zone-level transition is:

```text
OLD CURRENT RESULT
        ↓ transaction
NEW CURRENT RESULT
```

or, on failure:

```text
OLD CURRENT RESULT
        ↓ failed transaction
OLD CURRENT RESULT remains
```

This connects ownership directly to transaction scope.

## Change analysis

A generated result may become stale because of changes to:

- source reinforcement geometry;
- relevant grid geometry;
- active-view context;
- dimension/reference policy;
- layout policy;
- host/API constraints.

SSAD does not require reopening everything.

```text
changed claim/context
        ↓
affected owners
        ↓
recalculate current generated result
```

The generated annotation set is derived state whose validity depends on upstream canonical owners.

## General SSAD lesson

Many systems contain derived or generated state:

- search indexes;
- caches;
- projections/read models;
- generated documents;
- compiled artifacts;
- local offline snapshots;
- UI-derived state.

The key questions are the same:

```text
What source truth does it depend on?
Who owns the generated state?
Can users modify it independently?
What makes it stale?
How is it rebuilt or reconciled?
What is the atomic replacement boundary?
```

> **Derived state needs explicit ownership even when it can always be regenerated.**

Canonical project knowledge:
https://github.com/branch-danya-dev/revit-rebar-autodim-analysis/tree/main/regeneration

Back to: [`Rebar AutoDim application`](README.md)
