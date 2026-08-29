# Change impact checklist

Короткий маршрут для ситуации: **«Меняется существующая система. Что реально затронуто?»**

## 1. Отдели цель от реализации

- Какое поведение должно измениться?
- Что должно остаться неизменным?
- Является ли предложенная реализация обязательной?

## 2. Построй initial scope

- Какие responsibility zones точно затронуты?
- Какие owners нужно подключить?
- Какие данные, состояния и контракты участвуют?

## 3. Расширь до Change Surface

Проверь:

```text
Responsibilities
Ownership
Behavior
States
Data
Interfaces
Integrations
Flows
Trust
Failures
Operations
```

Классифицируй найденное:

```text
DIRECT
INDIRECT
POTENTIAL
OUT OF SCOPE
```

## 4. Проверь совместимость

- Сломается ли старый клиент?
- Нужна ли migration данных?
- Возможны ли mixed versions?
- Что будет при частичном rollout?
- Есть ли rollback path?
- Меняются ли trust assumptions или security boundaries?

## 5. Переоткрой только нужное знание

Для каждого затронутого утверждения спроси:

> Может ли это перестать быть истинным после изменения?

Если да — переоткрой canonical knowledge.

Если нет — оставь стабильным и при необходимости явно пометь `OUT OF SCOPE`.

## Минимальный результат

```text
Desired change
Must-not-change invariants
Initial scope
Change Surface
Affected owners
Compatibility risks
Reopened knowledge
Verification targets
```

## Куда идти дальше

- [`06-change/initial-scope`](../../06-change/initial-scope/)
- [`06-change/change-surface`](../../06-change/change-surface/)
- [`06-change/compatibility-risk`](../../06-change/compatibility-risk/)
- [`06-change/selective-reopening`](../../06-change/selective-reopening/)
