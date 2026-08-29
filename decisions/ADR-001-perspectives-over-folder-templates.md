# ADR-001 — Perspectives Over Folder Templates

> **Status:** Accepted  
> **Decision type:** Methodology architecture  
> **Origin:** Real-world application — Aveli  
> **Applies since:** SSAD v0.1.1

[Русская версия](ADR-001-perspectives-over-folder-templates.ru.md)

## Context

Early SSAD work used the Aveli repository structure as the first complete real-world application:

```text
business/
database/
backend/
frontend/
integrations/
system/
```

This structure worked for Aveli because those areas represented real responsibility and knowledge boundaries in that system.

The risk was to turn a successful application structure into a universal methodology template.

That would create several problems:

- systems without a backend or frontend would gain artificial directories;
- plugins, workers, gateways, infrastructure platforms, and operational systems would be forced into product-shaped terminology;
- documentation structure would start following methodology categories instead of the analyzed system;
- empty or weak directories would appear only to satisfy the template;
- ownership could become less clear rather than more clear.

Aveli demonstrated that useful SSAD rules are based on **analytical coverage and ownership**, not on fixed folder names.

Synthetic examples can now demonstrate the same rule across deliberately different system shapes.

## Decision

SSAD requires **analytical perspectives**, not a predefined repository tree.

A project MUST make the important system questions explicit, including where applicable:

```text
product / business intent
scope and system boundary
required behavior
data ownership and lifecycle
runtime responsibilities
internal interfaces
external integrations
technology usage
trust / security / failure constraints
acceptance and verification
whole-system relationships
```

The physical repository structure SHOULD follow the real owners of those concerns.

Possible structures include:

```text
Mobile application
├── business/
├── database/
├── backend/
├── frontend/
├── integrations/
└── system/
```

```text
Desktop plugin
├── business/
├── plugin/
├── host-application/
├── filesystem/
├── integrations/
└── system/
```

```text
Event-driven platform
├── business/
├── services/
├── messaging/
├── data/
├── infrastructure/
├── operations/
└── system/
```

None of these trees is canonical for SSAD.

The canonical requirement is that important analytical perspectives have explicit owners.

## Consequences

### Positive

- repository structure can reflect actual architecture;
- ownership remains meaningful across different system types;
- optional areas appear only when justified;
- the methodology can transfer between mobile, plugin, platform, enterprise, and other system shapes;
- synthetic examples can explore new shapes without changing the specification;
- documentation avoids empty directories created for methodological symmetry.

### Trade-offs

- two SSAD repositories may look structurally different;
- automated tooling cannot rely only on fixed folder names;
- cross-project automation will eventually require semantic metadata or conventions beyond path matching;
- authors must make an explicit ownership decision instead of copying a template.

## Evidence

### Real-world application

Aveli produced the original finding:

> **Analytical perspectives are required; folder templates are not.**

See:

[`../applications/aveli/methodology-findings.md`](../applications/aveli/methodology-findings.md)

### Synthetic examples

The following examples demonstrate the consequence across different system shapes:

- [`../examples/mobile-application/`](../examples/mobile-application/)
- [`../examples/desktop-plugin/`](../examples/desktop-plugin/)
- [`../examples/event-driven-platform/`](../examples/event-driven-platform/)

The examples illustrate the rule. The Aveli application provides real-world evidence that motivated it.

## Implications for Future SSAD Work

Reusable templates MAY suggest common analytical questions and document shapes.

They MUST NOT require every project to create the same top-level directories.

Future machine-readable SSAD metadata SHOULD identify semantic perspective and ownership independently from physical path.

## Decision Summary

> **SSAD standardizes the questions and ownership model that a system analysis must make explicit. It does not standardize one universal folder tree.**
