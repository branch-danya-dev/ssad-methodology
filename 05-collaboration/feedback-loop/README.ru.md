# Knowledge Feedback Loop

SSAD рассматривает реализацию, тестирование и эксплуатацию как источники нового evidence.

Поэтому жизненный цикл знания не заканчивается на specification или grooming.

```text
Analysis
  ↓
Specification
  ↓
Implementation
  ↓
Observed evidence
  ↓
Model check
  ↓
Knowledge update
```

## Почему feedback обязателен

Во время реализации могут выясниться факты, которых не было на этапе анализа:

- библиотека или provider не поддерживает предполагаемый механизм;
- существующая БД содержит дополнительное ограничение;
- integration API ведёт себя иначе, чем описано;
- QA обнаруживает неоднозначный transition;
- production показывает failure mode, которого не было в модели.

Если эти факты остаются только в коде, чате или памяти команды, SSAD перестаёт отражать реальную систему.

## Evidence → impact

Не каждое наблюдение требует перепроектирования.

Сначала определи, что именно оно затрагивает:

```text
Implementation detail only
→ canonical system knowledge may stay unchanged

Contract changed
→ interface knowledge reopens

State semantics changed
→ state + behavior knowledge reopen

Authority assumption invalidated
→ ownership / trust reopen

New failure mode discovered
→ failures + affected flows reopen
```

## Метод

```text
1. Зафиксируй новый evidence.
2. Сравни его с текущей моделью.
3. Определи затронутого canonical owner.
4. Реши: модель неверна или реализация отклонилась?
5. Если модель неверна — вернись в analysis.
6. Если реализация неверна — исправь implementation.
7. Повтори verification.
8. Обнови каноническое знание после подтверждения.
```

## Пример

Specification:

```text
Backend stores refresh token.
```

Во время реализации:

```text
Developer evidence:
Current identity provider does not expose refresh tokens.
```

Следствие:

```text
Assumption invalidated
↓
Auth behavior reopened
↓
Interface/provider constraints reopened
↓
Alternative session model selected
↓
Specification updated
↓
QA scenarios updated
```

Неправильный вариант — оставить спецификацию прежней и считать комментарий разработчика «технической деталью».

## Production тоже участвует

После релиза evidence может приходить из:

- logs;
- metrics;
- support incidents;
- user reports;
- integration errors;
- security events.

Operations и Support поэтому являются участниками knowledge loop, а не только downstream-потребителями системы.

## Когда loop закрыт

```text
Observed reality
        =
Verified implementation
        =
Canonical system knowledge
```

Полного идеального равенства достичь трудно, но именно к нему должен стремиться процесс.

> **Если реализация изменила наше понимание системы, работа над знанием ещё не закончена.**
