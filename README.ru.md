<div align="center">

# SSAD

### System-Structured Analysis Documentation

**Практическая методология системного анализа для реальной работы:**  
от первого запроса и требований — до реализации, проверки и актуального системного знания.

[English](README.md) · [Начать с Foundation](01-foundation/README.ru.md) · [Открыть Practice](07-practice/README.ru.md) · [Посмотреть Aveli](08-examples/aveli/README.ru.md)

</div>

---

> [!NOTE]
> **SSAD учит не писать документы.**  
> SSAD учит системно решать задачи в реальном цикле разработки, а документация становится структурированным следом анализа.

## Идея в одной схеме

```mermaid
flowchart LR
    S[Реальная система] --> B[Boundaries]
    B --> R[Responsibilities]
    R --> O[Ownership]
    O --> M[Local models]
    M --> C[Connections]
    C --> Y[System synthesis]
```

Главный принцип:

> **Структурируй знания так, как структурирована система. Для значимых фактов определяй канонического владельца. Локальные модели всегда собирай обратно в целостное представление системы.**

SSAD не задаёт универсальное дерево `requirements/`, `api/`, `database/`, `diagrams/`. Структура знания появляется после того, как понятны реальные границы и зоны ответственности конкретной системы.

---

## Куда идти

| Если тебе нужно... | Начни здесь |
|---|---|
| понять сам подход | [`01 · Foundation`](01-foundation/README.ru.md) |
| разобрать новую задачу от запроса до delivery | [`02 · Workflow`](02-workflow/README.ru.md) |
| глубоко проанализировать систему | [`03 · Analysis`](03-analysis/README.ru.md) |
| понять, где хранить знание | [`04 · Knowledge Structure`](04-knowledge-structure/README.ru.md) |
| провести review и работать с командой | [`05 · Collaboration`](05-collaboration/README.ru.md) |
| оценить влияние изменения | [`06 · Change`](06-change/README.ru.md) |
| получить короткий рабочий checklist | [`07 · Practice`](07-practice/README.ru.md) |
| увидеть SSAD на реальном проекте | [`08 · Examples`](08-examples/README.ru.md) |

### Первый последовательный проход

```text
Foundation
   ↓
Workflow
   ↓
Analysis
   ↓
Knowledge Structure
   ↓
Collaboration
   ↓
Change
   ↓
Practice + Examples
```

Уже работаешь над конкретной задачей? Не обязательно читать всё подряд — открой [`07-practice/`](07-practice/README.ru.md) и перейди в нужную глубокую главу из checklist.

---

## Реальный workflow системного аналитика

```mermaid
flowchart LR
    A[Pre-analysis] --> B[Requirements]
    B --> C[Analysis & Design]
    C --> D[Specification]
    D --> E[Review]
    E --> F[Grooming]
    F --> G[Delivery Support]
    G --> H[Verification]
    H --> I[Knowledge Update]

    E -. new evidence .-> C
    G -. implementation facts .-> C
    H -. mismatch .-> D
```

SSAD не подменяет delivery-процесс своим lifecycle. Она показывает, **какое системное знание должно появиться на каждом этапе, как его проверить и где оно должно жить**.

---

## Как SSAD анализирует систему

После определения границ и responsibility areas аналитик последовательно углубляется в нужные перспективы:

```text
Boundaries
→ Responsibilities
→ Ownership
→ Behavior
→ States
→ Data
→ Interfaces
→ Integrations
→ Flows
→ Trust
→ Failures
→ Synthesis
```

Это default reasoning order, а не waterfall. Новый факт может переоткрыть любой более ранний вопрос.

---

## Архитектура знания

SSAD разделяет две задачи:

```text
ИЕРАРХИЯ
→ где находится каноническое знание

ГРАФ ССЫЛОК
→ как знания связаны между собой
```

> **Хранение иерархично. Знание связано графом.**

Локальный документ может повторить необходимый контекст, чтобы оставаться читаемым, но не должен становиться второй независимой версией истины.

> **Не дублируй знание. При необходимости дублируй только контекст.**

---

## Команда ↔ SSAD

```mermaid
flowchart TD
    P[Product / Business / Client] <--> SA[System Analyst]
    SA <--> K[SSAD knowledge]
    K <--> D[Development]
    K <--> Q[QA]
    K <--> A[Architecture / Integration / Ops]
    D --> E[Implementation evidence]
    Q --> E
    A --> E
    E --> K
```

Разные участники приносят разное evidence и обладают разной authority.

Разработчик может быть лучшим источником факта о текущей реализации, но не обязательно владельцем продуктового или архитектурного решения. Review, grooming, разработка и QA поэтому не завершают анализ — они могут изменить его.

---

## Реальная проверка: Aveli

Основной real-world кейс SSAD — **Aveli**:

**[branch-danya-dev/aveli-system-analysis](https://github.com/branch-danya-dev/aveli-system-analysis)**

В нём SSAD проверяется не на искусственном шаблоне, а на настоящей системе с:

- Flutter frontend;
- backend-controlled account и access;
- локальным professional workspace;
- RevenueCat и store billing;
- offline trust;
- external integrations;
- failure behavior и end-to-end flows.

Начать компактный разбор: **[`08-examples/aveli/`](08-examples/aveli/README.ru.md)**.

```text
Repository structure
        ↓
Access ownership
        ↓
Offline trust
        ↓
System synthesis
```

---

## Что SSAD не пытается заменить

SSAD совместима с существующими инженерными практиками и инструментами.

Она не заменяет UML, BPMN, C4, OpenAPI, ADR, schemas, backlog, user stories или архитектурные стандарты команды.

Она отвечает на другой вопрос:

> **Как собрать разнородные аналитические знания в целостную, навигируемую и поддерживаемую модель конкретной системы?**

---

## Развитие проекта и contributions

SSAD сейчас находится в фазе **validation и stabilization**, а не бесконечного добавления новых глав.

- Хочешь участвовать в развитии? Открой [`CONTRIBUTING.ru.md`](CONTRIBUTING.ru.md).
- Хочешь понять, что именно будет означать готовность к v1.0? Открой [`ROADMAP.ru.md`](ROADMAP.ru.md).

Главное правило дальнейшего развития:

> **Новые концепты должны появляться из реальных аналитических friction points и evidence, а не из желания закончить классификацию.**

Текущий путь к v1.0 делает приоритетом второй real-world validation case, дальнейшее применение SSAD к изменениям Aveli, стабильность терминологии и навигации, а также осознанный выбор publication license.

---

## Активная структура репозитория

```text
01-foundation/          principles
02-workflow/            real SA lifecycle
03-analysis/            analytical toolkit
04-knowledge-structure/ knowledge architecture
05-collaboration/       team ↔ knowledge loop
06-change/              change mechanics
07-practice/            task-based checklists
08-examples/            real-world validation
assets/                 supporting visuals
```

Исторические версии структуры остаются в Git history и не конкурируют с текущим знанием.

---

<div align="center">

**Начать:** [`01 · Foundation`](01-foundation/README.ru.md)  
**Есть задача прямо сейчас:** [`07 · Practice`](07-practice/README.ru.md)  
**Хочется увидеть реальный проект:** [`08 · Aveli`](08-examples/aveli/README.ru.md)  
**Участвовать:** [`CONTRIBUTING`](CONTRIBUTING.ru.md) · **Направление:** [`ROADMAP`](ROADMAP.ru.md)

</div>
