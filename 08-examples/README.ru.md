# 08 · Examples and Applications

[English version](README.md)

Этот раздел показывает, **как SSAD выглядит на практике и выдерживает проверку разными реальными системами**.

Examples и applications нужны не как витрина и не как набор шаблонов для копирования.

Их задача — проверить, складываются ли принципы из предыдущих разделов в рабочую модель анализа на системах разной формы.

## Два типа validation material

```text
Synthetic example
→ дешёвое исследование одной сфокусированной идеи

Real-world application
→ проверка на настоящей системе,
  реальных ограничениях и реальном ownership
```

Synthetic examples полезны для обучения отдельным конструкциям.

Сама методология должна подтверждаться несколькими real-world applications.

## Real-world applications

### Aveli · product-shaped system

Полный репозиторий:

https://github.com/branch-danya-dev/aveli-system-analysis

Aveli проверяет SSAD на software product с frontend, backend, локальными профессиональными данными, server-owned access, billing, offline trust и external integrations.

Структура знания появилась из собственных responsibility areas системы:

```text
business/
database/
backend/
frontend/
integrations/
system/
```

Компактный маршрут:

```text
Repository Structure
        ↓
Access Ownership
        ↓
Offline Trust
        ↓
System Synthesis
```

→ [`Aveli · end-to-end application`](aveli/README.ru.md)

### Enterprise Workplace Migration · transformation-shaped system

Полный репозиторий:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

Этот кейс проверяет SSAD на распределённой enterprise migration programme, где ни одно приложение не владеет всей системой.

Его responsibility areas отличаются от Aveli:

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

Компактный маршрут:

```text
Responsibility Structure
        ↓
Global Status Decomposition
        ↓
Evidence & Readiness
        ↓
Technical Projection
```

→ [`Enterprise Workplace Migration · application`](enterprise-workplace-migration/README.ru.md)

## Почему два application важны вместе

Ценность не в том, что оба репозитория выглядят одинаково. Наоборот, они намеренно разные.

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
```

Общая методология проявляется в reasoning model, а не в обязательном дереве директорий.

> **Одинаковые аналитические принципы. Разная system-shaped knowledge architecture.**

## Главное правило applications

Application может:

- упростить контекст;
- выделить один аналитический вопрос;
- показать схему;
- объяснить ход рассуждения;
- сравнить модель до и после применения SSAD.

Но application не должен становиться второй канонической версией проектного знания.

> **Теория объясняется через application. Истина проекта остаётся у канонического владельца.**

Поэтому каждый application ведёт обратно в полный проектный репозиторий и соответствующие главы SSAD.

## Выбрать маршрут

```text
Нужен software-product кейс?
→ Aveli

Нужен enterprise migration / distributed-ownership кейс?
→ Enterprise Workplace Migration
```

Вернуться к началу: [`README.ru.md`](../README.ru.md)
