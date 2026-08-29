# Review & Grooming checklist

Короткий маршрут для ситуации: **«Нужно проверить решение с командой и подготовить его к реализации.»**

## Review: корректно ли решение?

Проверь по перспективам:

```text
Business     → решаем ли правильную проблему?
Architecture → корректны ли границы и зависимости?
Development  → реализуемы ли контракты и поведение?
QA           → однозначно ли поведение и можно ли его проверить?
Integration  → корректны ли внешние границы и контракты?
Security     → корректны ли trust assumptions и доступ?
Operations   → можно ли это наблюдать, выкатывать и восстанавливать?
```

### Вопросы review

- Все ли affected responsibilities найдены?
- Ownership определён?
- Happy path и альтернативные пути описаны?
- Состояния и переходы непротиворечивы?
- Ошибки и degraded behavior заданы?
- Сквозной flow сходится?
- Есть ли непроверенные assumptions?

## Grooming: одинаково ли команда понимает реализацию?

- Понятен scope задачи?
- Понятно, что явно не входит в scope?
- Известны зависимости?
- Контракты достаточно конкретны?
- Acceptance criteria проверяемы?
- Open questions закрыты или имеют владельцев?
- Нет ли скрытой работы, которую разные участники понимают по-разному?

## Ready check

```text
Purpose understood        ✓
Scope defined             ✓
Affected components known ✓
Ownership defined         ✓
Contracts described       ✓
States / edge cases known ✓
Open questions resolved   ✓
Acceptance criteria clear ✓
Dependencies known        ✓
```

Если в review обнаружен новый факт, не «исправляй текст локально». Вернись к каноническому владельцу знания и переоткрой соответствующую часть анализа.

## Куда идти дальше

- [`02-workflow/04-review`](../../02-workflow/04-review/)
- [`02-workflow/05-grooming`](../../02-workflow/05-grooming/)
- [`05-collaboration/validation`](../../05-collaboration/validation/)
- [`05-collaboration/decision-resolution`](../../05-collaboration/decision-resolution/)
