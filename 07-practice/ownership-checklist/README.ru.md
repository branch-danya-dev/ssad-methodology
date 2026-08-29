# Ownership checklist

Короткий маршрут для ситуации: **«Я не понимаю, кто на самом деле владеет этим состоянием или решением.»**

## Основные вопросы

- Кто принимает решение?
- Кто хранит каноническое состояние?
- Кто имеет право его изменить?
- Кто только сообщает evidence?
- Кто потребляет результат?
- Кто подтверждает корректность?

## Проверка на ложный ownership

Не называй владельцем систему только потому, что она:

- первой получила данные;
- физически хранит копию;
- показывает значение в UI;
- инициирует запрос;
- технически может изменить поле.

Ownership определяется **authority и ответственностью за истину**, а не расположением данных.

## Если владельцев несколько

Проверь, не смешаны ли разные виды знания:

```text
Business decision
System state
External evidence
Derived state
Cached copy
Presentation state
```

У каждого из них может быть свой canonical owner.

## Минимальный результат

```text
Knowledge/state
Canonical owner
Decision authority
Allowed writers
Evidence sources
Consumers
Validation source
```

## Куда идти дальше

- [`03-analysis/ownership`](../../03-analysis/ownership/)
- [`04-knowledge-structure/canonical-ownership`](../../04-knowledge-structure/canonical-ownership/)
- [`05-collaboration/knowledge-contribution`](../../05-collaboration/knowledge-contribution/)
