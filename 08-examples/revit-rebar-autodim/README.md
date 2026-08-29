# Rebar AutoDim · host-application automation application

[Русская версия](README.ru.md)

This application shows how SSAD behaves on a **host-application automation system** implemented inside Autodesk Revit.

Full project repository:

https://github.com/branch-danya-dev/revit-rebar-autodim-analysis

Rebar AutoDim automates dimensioning of rectangular `Area Reinforcement` zones on the active Revit view. The interesting SSAD problem is not the dimension algorithm by itself. It is the ownership boundary between:

```text
Autodesk Revit
→ owns model/view state, native element validity,
  geometric references and transaction semantics

Rebar AutoDim
→ owns interpretation of that evidence for one annotation problem,
  dimension intent, generated annotation state and regeneration rules
```

This system shape is materially different from both Aveli and Enterprise Workplace Migration.

## Why this application matters

A host plugin cannot pretend to own the environment in which it executes.

It must distinguish:

```text
host evidence
!= plugin decision

semantic target
!= host API representation

valid analysis
!= successfully committed native output

source model state
!= generated plugin-owned state
```

Those distinctions test whether SSAD can remain implementation-aware without letting framework/API mechanics become the canonical system model.

## Repository structure after applying SSAD

The project is organized around stable analytical responsibilities:

```text
system/
execution-context/
geometry/
references/
layout/
annotations/
regeneration/
revit-boundary/
evidence/
```

This is not an SSAD template. It emerged from the actual questions of this system.

## Compact application route

```text
Host Boundary
      ↓
View-Space Geometry
      ↓
Semantic Reference vs API Reference
      ↓
Generated Output Ownership
```

### 1. Host Boundary

Revit is both the source of structural evidence and the authority that decides whether a native reference, dimension or transaction is valid.

Rebar AutoDim owns only its narrow analytical transformation and its generated annotation layer.

→ [`Host Boundary`](host-boundary.md)

### 2. View-Space Geometry

The structural model owns geometry, but the **active view defines the annotation frame** in which width, height, left/right and placement are interpreted.

This makes the active view part of system meaning rather than a passive API parameter.

→ [`View-Space Geometry`](view-space-geometry.md)

### 3. Semantic Reference vs API Reference

The system must first decide **what should be dimensioned** and only then determine which Revit `Reference` can technically realize that intent.

Supporting detail geometry is therefore an API adaptation, not a new owner of geometric truth.

→ [`Semantic Reference`](semantic-reference.md)

### 4. Generated Output Ownership

The source reinforcement remains owned by the structural model. Rebar AutoDim owns one current generated annotation result per source zone and replaces that result on rerun instead of accumulating duplicates.

→ [`Generated Output Ownership`](generated-output-ownership.md)

## What this validates in SSAD

This application adds evidence that SSAD can model systems where:

- the analyzed system executes inside a stronger host authority;
- the host owns low-level validity while the plugin owns domain interpretation;
- geometry meaning depends on execution context;
- semantic decisions require translation into framework-specific representations;
- generated state has ownership independent from source state;
- transaction atomicity defines meaningful failure boundaries;
- implementation constraints may force adaptations without becoming the owner of system meaning.

## Compared with the other real-world applications

```text
Aveli
→ product-shaped software system
→ application-owned services/data + external providers

Enterprise Workplace Migration
→ transformation-shaped enterprise system
→ distributed evidence + cross-team decisions

Rebar AutoDim
→ host-application automation system
→ external host authority + local semantic transformation
```

The common structure is not a folder tree.

The common structure is the reasoning discipline:

```text
Boundaries
→ Responsibilities
→ Ownership
→ Local models
→ Connections
→ Failures
→ Synthesis
```

## Canonical truth

This directory is methodology validation material.

Canonical Rebar AutoDim project knowledge remains in:

https://github.com/branch-danya-dev/revit-rebar-autodim-analysis

> **An SSAD application explains what the methodology revealed. It does not become a second project specification.**

Back to: [`08 · Examples and Applications`](../README.md)
