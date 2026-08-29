# Contributing to SSAD

[Русская версия](CONTRIBUTING.ru.md)

Thank you for considering a contribution to SSAD.

SSAD is a system-analysis methodology, not a catalog of document templates. Contributions should make the methodology easier to understand, validate or apply without turning it into a rigid universal standard.

## Before opening a change

Please identify which kind of contribution you are making:

- **clarification** — improve wording without changing meaning;
- **method improvement** — improve how an analytical problem is approached;
- **practice improvement** — add or refine a task-oriented checklist;
- **example** — demonstrate an existing SSAD principle on a concrete system;
- **consistency fix** — align terminology, navigation or RU/EN parity;
- **methodology change** — change a principle, responsibility boundary or reasoning model.

The last category deserves the most scrutiny because it can affect multiple chapters.

## Contribution principles

### 1. Change the owner, not every mention

If a canonical rule changes, update its canonical owner first. Neighboring chapters should normally update only their context or links.

> Do not create a second truth to make a local chapter self-contained.

### 2. Prefer system questions over artifact taxonomies

A proposal should be framed around a real analytical question:

```text
What system problem does this solve?
Which responsibility owns the knowledge?
How does the analyst apply it?
How can the result be verified?
```

Avoid adding a new top-level category only because a familiar document type exists in another methodology.

### 3. Preserve progressive depth

Root and overview files should remain compact. Detailed reasoning belongs in the chapter that owns it.

A reader should be able to:

```text
overview
→ choose a question
→ open the relevant chapter
→ follow links only when deeper context is needed
```

### 4. Evidence before abstraction

New methodology concepts should preferably be supported by one or more of:

- repeated real-world analytical problems;
- a concrete project case;
- a contradiction or limitation in the current model;
- implementation / QA / operations evidence;
- a clear reduction in ambiguity or analytical cost.

Do not add abstractions only to make the taxonomy feel more complete.

### 5. Keep RU and EN semantically equivalent

Exact sentence-by-sentence translation is not required, but both versions should carry the same methodology:

- same responsibility;
- same reasoning method;
- same important examples;
- same completion criteria;
- same navigation intent.

## Pull request checklist

Before submitting a PR, check:

- [ ] The change has a clear analytical purpose.
- [ ] The canonical owner of the changed knowledge is clear.
- [ ] No competing duplicate truth was introduced.
- [ ] Neighboring chapters are linked instead of copied when possible.
- [ ] RU and EN remain semantically aligned where both exist.
- [ ] Examples are labeled as examples and do not become project truth.
- [ ] Navigation still follows progressive depth.
- [ ] The change does not introduce a universal folder/template requirement without strong evidence.
- [ ] The resulting methodology can still be explained in practical system-analysis terms.

## What usually does not belong in SSAD

SSAD does not need to re-document external standards or tools in full.

For example, contributions should not turn the repository into a replacement manual for:

- UML;
- BPMN;
- C4;
- OpenAPI;
- SQL;
- ADR;
- Jira / backlog practices;
- architecture frameworks.

SSAD may explain **when and why** such tools help answer a system question, then link outward or use a small example.

## Examples and case studies

Examples should answer:

```text
What SSAD principle is being demonstrated?
What real system question is involved?
What was the reasoning path?
Where does canonical project knowledge live?
```

Real project truth should remain in the project repository whenever possible.

## Methodology changes

A methodology-level proposal should explain:

1. the current limitation;
2. evidence that the limitation is real;
3. the proposed change;
4. which chapters and concepts are affected;
5. what becomes simpler or more correct;
6. possible regressions or new ambiguity;
7. how the change can be validated on a real case.

Small wording improvements do not need this level of ceremony.

## Review mindset

A good SSAD review asks more than “is the text good?”

It asks:

```text
Is the system meaning correct?
Is ownership clear?
Does the method help an analyst act?
Does this duplicate existing knowledge?
Does it preserve the shape of the methodology?
Can the idea survive a real system example?
```

## Where to start

- methodology principles: [`01-foundation/`](01-foundation/)
- real analyst workflow: [`02-workflow/`](02-workflow/)
- analytical mechanics: [`03-analysis/`](03-analysis/)
- practical checklists: [`07-practice/`](07-practice/)
- real-world validation: [`08-examples/`](08-examples/)
- project direction: [`ROADMAP.md`](ROADMAP.md)
