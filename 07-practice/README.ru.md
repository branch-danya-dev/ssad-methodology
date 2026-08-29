# 07 · Practice

Этот раздел превращает SSAD в **ежедневный рабочий инструмент системного аналитика**.

Он не повторяет теорию из Workflow, Analysis, Knowledge Structure, Collaboration и Change. Его задача — дать короткий вход в методологию из конкретной рабочей ситуации.

## Как пользоваться

Начни не с термина SSAD, а с вопроса, который у тебя возник на работе.

```text
Рабочая ситуация
      ↓
короткий checklist
      ↓
минимальный результат
      ↓
ссылки на глубокую теорию
```

## Быстрые маршруты

### Мне пришла новая задача

Открой [`pre-analysis-checklist/`](pre-analysis-checklist/).

Помогает быстро определить:
- проблему и ожидаемый результат;
- initial scope;
- известных участников и ограничения;
- факты, assumptions и open questions.

### Нужно проанализировать интеграцию

Открой [`integration-checklist/`](integration-checklist/).

Проверяет:
- ownership boundary;
- contract semantics;
- evidence vs authority;
- retry/idempotency;
- trust;
- failure/recovery;
- reconciliation.

### Непонятно, кто владеет состоянием или решением

Открой [`ownership-checklist/`](ownership-checklist/).

Помогает отделить:
- canonical owner;
- decision authority;
- allowed writers;
- evidence sources;
- consumers.

### Нужно спроектировать или проверить API

Открой [`api-contract-checklist/`](api-contract-checklist/).

Маршрут идёт от семантики операции к request/response, errors, state effects, idempotency и compatibility.

### Иду на Review или Grooming

Открой [`review-grooming-checklist/`](review-grooming-checklist/).

Разделяет два вопроса:

```text
Review
→ корректно ли решение?

Grooming
→ одинаково ли команда понимает реализацию?
```

### Меняется существующая система

Открой [`change-impact-checklist/`](change-impact-checklist/).

Помогает построить Change Surface, оценить compatibility/risk и определить, какое каноническое знание действительно нужно переоткрыть.

## Что Practice не делает

Practice не должен превращаться в коллекцию универсальных шаблонов, которые нужно заполнять целиком.

Checklist — это **навигационный и мыслительный инструмент**, а не обязательная форма документа.

Если вопрос прост, используй только нужную часть списка. Если задача сложная — переходи по ссылкам в соответствующие главы методологии.

## Принцип

> **Practice начинается с рабочей ситуации и ведёт к нужной глубине анализа, а не заставляет вспоминать структуру методологии.**

Следующий раздел: [`08-examples/`](../08-examples/).
