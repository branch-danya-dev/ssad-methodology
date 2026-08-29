# 08 · Examples and Applications

[Русская версия](README.ru.md)

This section shows **what SSAD looks like in practice and whether it survives contact with different real systems**.

Examples and applications are not a showcase and not a collection of templates to copy.

Their purpose is to test whether the principles from the previous sections combine into a workable analysis model across systems with different shapes.

## Two kinds of validation material

```text
Synthetic example
→ inexpensive exploration of one focused idea

Real-world application
→ validation against an actual system,
  real constraints and real ownership
```

Synthetic examples are useful for teaching isolated concepts.

The methodology itself should be validated by multiple real-world applications.

## Real-world applications

### Aveli · product-shaped system

Full repository:

https://github.com/branch-danya-dev/aveli-system-analysis

Aveli validates SSAD on a software product containing frontend, backend, local professional data, server-owned access, billing, offline trust and external integrations.

Its knowledge structure emerged from its own responsibility areas:

```text
business/
database/
backend/
frontend/
integrations/
system/
```

Compact application route:

```text
Repository Structure
        ↓
Access Ownership
        ↓
Offline Trust
        ↓
System Synthesis
```

→ [`Aveli · end-to-end application`](aveli/README.md)

### Enterprise Workplace Migration · transformation-shaped system

Full repository:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

This case validates SSAD on a distributed enterprise migration programme where no single application owns the whole system.

Its responsibility areas are different from Aveli:

```text
system/
workplace/
readiness/
planning/
execution/
exceptions/
integrations/
technical-projection/
```

Compact application route:

```text
Responsibility Structure
        ↓
Global Status Decomposition
        ↓
Evidence & Readiness
        ↓
Technical Projection
```

→ [`Enterprise Workplace Migration · application`](enterprise-workplace-migration/README.md)

### Rebar AutoDim · host-application automation system

Full repository:

https://github.com/branch-danya-dev/revit-rebar-autodim-analysis

Rebar AutoDim validates SSAD on a plugin that executes inside Autodesk Revit, consumes host-owned geometry and API capabilities, and produces its own regenerable native annotation state.

Its responsibility areas emerged around a different set of system questions:

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

Compact application route:

```text
Host Boundary
        ↓
View-Space Geometry
        ↓
Semantic Reference
        ↓
Generated Output Ownership
```

→ [`Rebar AutoDim · application`](revit-rebar-autodim/README.md)

## Why the three applications matter together

The value is not that the repositories look similar. They deliberately do not.

```text
Aveli
→ product boundaries
→ frontend/backend/local-data ownership
→ billing evidence vs access authority
→ bounded offline trust

Enterprise migration
→ distributed operational boundaries
→ cross-team evidence
→ readiness as aggregate decision
→ planning vs execution separation
→ exception/recovery paths
→ technical projection corrected by domain ownership

Rebar AutoDim
→ host-application boundary
→ view-context-dependent geometry meaning
→ semantic target vs API representation
→ generated-state ownership
→ transaction-scoped failure isolation
```

The shared methodology appears in the reasoning model, not in a mandatory folder tree.

> **Same analytical principles. Different system-shaped knowledge architecture.**

The third application also adds a new kind of validation: a host can own native validity and execution mechanics without owning the plugin's analytical meaning.

## Main rule for applications

An application may:

- simplify context;
- isolate one analytical question;
- show a diagram;
- explain the reasoning path;
- compare the model before and after applying SSAD.

But it must not become a second canonical version of project knowledge.

> **Theory is explained through an application. Project truth remains with its canonical owner.**

Each application therefore links back to the full project repository and the relevant SSAD chapters.

## Choose a route

```text
Want a software-product case?
→ Aveli

Want an enterprise migration / distributed-ownership case?
→ Enterprise Workplace Migration

Want a host-application / plugin case?
→ Rebar AutoDim
```

Back to: [`README.md`](../README.md)
