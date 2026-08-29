# Selective Reopening

После определения Change Surface и рисков возникает практический вопрос:

> **Какие ранее стабильные области знания нужно открыть заново, а какие можно оставить неизменными?**

## Идея

SSAD не требует перепроверять всю систему после каждого изменения.

Вместо этого переоткрываются только те canonical knowledge areas, чьи утверждения могли перестать быть истинными.

```text
CHANGE SURFACE
      ↓
AFFECTED CLAIMS
      ↓
CANONICAL OWNERS
      ↓
REOPEN ONLY NECESSARY KNOWLEDGE
      ↓
REVALIDATE
      ↓
STABILIZE
```

## Что значит «переоткрыть знание»

Это не обязательно означает переписать документ.

Это означает снова считать утверждение **неподтверждённым до проверки**.

Например:

```text
Stable claim:
Backend is the authority for access decisions.

Change:
offline trust window expands.

Reopened knowledge:
trust policy,
client degraded behavior,
reconciliation assumptions.

Not reopened:
professional workspace ownership.
```

## Метод

Для каждого элемента Change Surface:

1. Найдите canonical owner знания.
2. Определите конкретные утверждения, на которые влияет изменение.
3. Маркируйте их как requiring revalidation.
4. Проверьте связанные contracts / flows / invariants.
5. После review, implementation evidence и verification стабилизируйте новую версию знания.

## Полезные статусы

Можно использовать простую модель:

```text
STABLE
REOPENED
VALIDATING
UPDATED
STABILIZED
```

Это не обязательный workflow-движок, а способ явно показать epistemic state знания.

## Почему это важно

Без selective reopening обычно происходят две крайности.

### Крайность 1: ничего не переоткрывать

Документация остаётся прежней, хотя система уже изменилась.

### Крайность 2: переоткрывать всё

Любая задача превращается в повторный анализ всей системы.

Оба подхода плохо масштабируются.

## Stabilization

Знание снова становится стабильным не после редактирования Markdown, а после появления достаточного evidence.

```text
Updated analytical decision
        ↓
Team validation
        ↓
Implementation
        ↓
Verification / observed behavior
        ↓
Canonical knowledge update
        ↓
STABILIZED
```

## Пример Aveli

Изменение:

> backend начинает принимать новый billing evidence source.

Переоткрыть нужно:

- billing evidence interpretation;
- reconciliation flow;
- access decision inputs;
- integration trust assumptions;
- failure/retry behavior.

Не обязательно переоткрывать:

- local workspace storage;
- frontend navigation;
- unrelated account profile fields.

## Проверка завершения изменения

```text
[ ] Change Surface проверена
[ ] affected canonical claims определены
[ ] нужные области переоткрыты
[ ] unaffected areas явно не затронуты
[ ] новые решения прошли validation
[ ] implementation evidence учтён
[ ] regression/invariants проверены
[ ] canonical knowledge обновлено
[ ] переоткрытые области снова стабилизированы
```

## Главный принцип

> **Изменение открывает не документы. Изменение открывает утверждения о системе, которые могли перестать быть истинными.**

Далее: [`07-practice/`](../../07-practice/).
