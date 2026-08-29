# 05 · Collaboration

Этот раздел отвечает на вопрос:

> **Как системно-аналитическое знание создаётся, проверяется и изменяется вместе с реальной командой?**

SSAD не рассматривает документацию как личный архив аналитика и не предполагает одноразовую передачу готового документа в разработку.

Команда является одновременно:

- источником knowledge и evidence;
- механизмом проверки модели;
- источником новых ограничений;
- участником принятия решений;
- источником implementation и production feedback.

## Базовый цикл

```text
KNOWLEDGE CONTRIBUTION
кто и что способен подтвердить?
        ↓
VALIDATION
какие утверждения выдерживают проверку?
        ↓
DECISION RESOLUTION
что делать с противоречиями?
        ↓
IMPLEMENTATION / QA / OPERATIONS
что показала реальная система?
        ↓
FEEDBACK LOOP
какое каноническое знание нужно обновить?
        ↺
```

## 1. Knowledge Contribution

[`knowledge-contribution/`](knowledge-contribution/)

Главный вопрос взаимодействия не «с кем поговорить?», а:

> **Какое знание этот участник способен подтвердить, опровергнуть или дополнить?**

Например:

```text
Product
→ business authority

Developer
→ implementation evidence

Architect
→ architecture authority

QA
→ ambiguity / edge cases / testability

Integration Owner
→ external contract evidence and authority
```

SSAD отдельно различает **evidence** и **authority**.

## 2. Validation

[`validation/`](validation/)

Команда проверяет не текст документа, а утверждения о системе.

```text
Business
→ правильно ли понята проблема?

Architecture
→ корректны ли boundaries и dependencies?

Development
→ реализуемо ли решение?

QA
→ однозначно ли поведение?

Integration Owner
→ корректен ли внешний контракт?
```

Review — один из механизмов validation, но validation происходит на всём workflow.

## 3. Decision Resolution

[`decision-resolution/`](decision-resolution/)

Разные участники могут давать несовместимые ответы.

SSAD предлагает не голосовать, а определить:

```text
conflicting claims
↓
evidence / authority / constraints
↓
alternatives
↓
consequences
↓
decision owner
↓
decision
↓
canonical knowledge update
```

Decision record хранит rationale. Каноническая модель хранит текущую истину.

## 4. Knowledge Feedback Loop

[`feedback-loop/`](feedback-loop/)

Разработка, QA и эксплуатация создают новый evidence.

```text
Analysis
→ Specification
→ Implementation
→ Evidence
→ Model check
→ Verification
→ Knowledge update
```

Если новый факт опровергает предположение, соответствующая область анализа должна быть переоткрыта.

## Участники

В зависимости от системы knowledge loop может включать:

```text
Client / Requester
Product / Business
Business Analyst
System Analyst
Architect
Developer
QA
DevOps / Operations
Security
Integration Owner
Support
```

SSAD не задаёт универсальную RACI-матрицу. Важнее определить **knowledge owner, evidence source и decision authority для конкретного вопроса**.

## Связь с Workflow

`02-workflow` отвечает: **когда взаимодействие происходит**.

`05-collaboration` отвечает: **как именно знание движется между людьми и SSAD**.

Например:

```text
Requirements
→ knowledge contribution + validation

Review
→ focused validation + decision resolution

Grooming
→ shared understanding validation

Delivery Support
→ implementation feedback

Verification
→ evidence against agreed model

Knowledge Update
→ canonical stabilization
```

## Главный принцип

> **Системное знание не передаётся команде как законченный артефакт. Оно создаётся, проверяется и развивается вместе с командой.**

Следующий раздел: [`06-change/`](../06-change/).
