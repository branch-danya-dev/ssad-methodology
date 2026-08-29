# SSAD Roadmap

[Русская версия](ROADMAP.ru.md)

This roadmap describes **methodology maturity**, not a feature backlog.

The goal is not to keep adding chapters. The goal is to prove that SSAD is coherent, teachable, practical and stable enough to use across different systems.

## Current stage

SSAD now has a complete reader-first backbone:

```text
Foundation
→ Workflow
→ Analysis
→ Knowledge Structure
→ Collaboration
→ Change
→ Practice
→ Examples
```

Two materially different real-world applications are now documented:

```text
Aveli
→ product-shaped software system

Enterprise Workplace Migration
→ distributed enterprise transformation / existing-system migration
```

The current phase is therefore **comparative validation and stabilization**: identify what remains stable across both systems, collect friction points and change the core only when evidence requires it.

## What v1.0 should mean

SSAD v1.0 should mean:

> **The core methodology is stable enough that future changes are mostly clarifications, stronger evidence, better examples and incremental practice guidance — not repeated redesign of the conceptual backbone.**

### v1.0 criteria

#### 1. Conceptual stability

- [ ] Foundation principles no longer require structural rewrites.
- [ ] Workflow and analytical mechanics do not compete as alternative lifecycles.
- [ ] Boundaries, responsibility, ownership, evidence, authority and canonical knowledge are used consistently.
- [ ] Local analysis and system synthesis have clear responsibilities.
- [ ] Change analysis reuses the same core model rather than introducing a parallel methodology.

#### 2. Real-world validation

- [ ] Aveli continues to validate the methodology after meaningful system changes.
- [x] At least one additional real-world system with a substantially different shape is documented as validation evidence.
- [x] At least one integration-heavy or event-driven case tests cross-boundary reasoning.
- [x] At least one existing-system / migration case tests Change Surface, compatibility and selective reopening.

Validation evidence now includes:

- [`08-examples/aveli/`](08-examples/aveli/) — product boundaries, access ownership and bounded offline trust;
- [`08-examples/enterprise-workplace-migration/`](08-examples/enterprise-workplace-migration/) — distributed responsibility, readiness evidence, state decomposition, migration/change reasoning and ownership-aware technical projection.

The second application matters because it demonstrates that SSAD can produce a system-shaped repository that looks nothing like Aveli while preserving the same reasoning principles.

#### 3. Learning quality

- [ ] A new analyst can follow Foundation → Workflow → Analysis without external explanation.
- [ ] Every core chapter has a clear problem, method, example and verification condition.
- [ ] Practice checklists reliably point back to deeper canonical chapters.
- [ ] RU and EN are semantically equivalent for all core content.
- [ ] Important terms are discoverable from context without requiring a giant glossary.

#### 4. Navigation quality

- [ ] Root README remains a compact landing page.
- [ ] No active legacy documentation competes with the reader-first structure.
- [ ] Cross-links reflect actual knowledge relationships instead of decorative linking.
- [ ] Readers can answer a local question without traversing unrelated sections.
- [ ] A large repository still feels locally small.

#### 5. Contribution model

- [x] Contribution principles are documented.
- [ ] Methodology-level proposals have a repeatable evidence and review process.
- [ ] Example contributions clearly separate teaching context from canonical project truth.
- [ ] Public issue / discussion conventions are defined once real external contributions begin.

#### 6. Publication readiness

- [ ] A publication license is intentionally selected and added.
- [ ] Repository description and topics clearly communicate system analysis, knowledge architecture and methodology scope.
- [ ] A stable v1.0 release is tagged with a concise release note.
- [ ] The changelog distinguishes historical research phases from the stable reader-first methodology.

## Near-term priorities

### P0 — compare, validate, do not expand

1. keep using SSAD on meaningful changes in Aveli and other real systems;
2. compare friction points between product-shaped and transformation-shaped applications;
3. identify ambiguity, duplication and missing reasoning steps that repeat across cases;
4. fix only issues supported by evidence.

### P1 — broaden validation only when it tests a new risk

The second real-world application milestone is complete.

A third case is useful only if it tests a materially new concern rather than adding another showcase.

Possible future validation shapes include:

- strongly event-driven backend platform;
- desktop or host-application plugin ecosystem;
- integration-heavy internal service with versioned contracts;
- system with significant data migration or distributed consistency concerns.

The question is no longer “do we have another case?” but:

> **Which untested system property could still break the current SSAD model?**

### P2 — contribution and release hygiene

- decide licensing;
- define issue/discussion conventions if external participation starts;
- establish release/versioning semantics;
- prepare v1.0 release notes when the criteria above are met.

## What is intentionally not on the roadmap

SSAD does **not** currently aim to add a dedicated top-level chapter for every analytical artifact, notation or technology.

There is no roadmap item such as:

```text
09-UML
10-BPMN
11-SQL
12-Kafka
13-OpenAPI
```

Those tools may appear inside relevant system questions and examples.

A new methodology area should exist only when it owns a distinct analytical responsibility that cannot be handled cleanly by the existing model.

## How roadmap items are accepted

A roadmap proposal should answer:

```text
What real problem appeared?
Which current SSAD area failed to handle it?
What evidence supports the problem?
Is a new concept actually needed?
Can an existing owner be improved instead?
How will the change be validated?
```

## Long-term direction

The desired mature form of SSAD is small at the conceptual core and rich at the evidence layer:

```text
stable principles
+
stable reasoning model
+
strong navigation
+
many real-world validations
+
practical task routes
```

Not:

```text
ever-growing taxonomy
+
ever-growing mandatory structure
```

That distinction is central to the project.
