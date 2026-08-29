# Validation

Validation — это проверка системного знания теми участниками, которые способны увидеть его слабые места с разных сторон.

> Цель validation — не получить формальное «согласовано», а обнаружить неверные предположения до реализации.

## Разные участники проверяют разное

```text
Business
→ правильно ли понята проблема и ожидаемое поведение?

Architecture
→ корректны ли границы и зависимости?

Development
→ реализуемы ли контракты и поведение?

QA
→ однозначно ли поведение и можно ли его проверить?

Integration Owner
→ корректно ли описано взаимодействие с внешней системой?

Security / Operations
→ учтены ли trust, failure и эксплуатационные ограничения?
```

Это не означает, что каждый документ должен пройти через всех. Нужные валидаторы определяются **затронутым знанием и риском ошибки**.

## Что валидируется

Validation может применяться к:

- scope и boundaries;
- responsibilities и ownership;
- бизнес-правилам;
- состояниям и переходам;
- данным и lifecycle;
- интерфейсам и интеграциям;
- failure behavior;
- trust assumptions;
- acceptance criteria;
- end-to-end flows.

## Метод

Для значимого решения:

```text
1. Определи утверждение или модель.
2. Определи, какой тип ошибки в ней возможен.
3. Найди участника, способного обнаружить эту ошибку.
4. Покажи не весь объём документации, а нужный контекст.
5. Зафиксируй результат: confirmed / changed / rejected / open.
6. Обнови каноническое знание.
```

## Review — один из механизмов validation

Workflow-этап Review использует этот механизм, но validation шире review.

Проверка может происходить:

- во время requirements;
- при проектировании API;
- в разговоре с integration owner;
- во время grooming;
- при разработке;
- во время QA;
- после production evidence.

## Ready Check

Для задачи, которая должна уйти в реализацию, полезна компактная проверка:

```text
Purpose understood        ✓
Scope defined             ✓
Affected components known ✓
Ownership defined         ✓
Behavior described        ✓
Contracts described       ✓
States / edge cases known ✓
Dependencies known        ✓
Acceptance criteria clear ✓
Critical OPENs resolved   ✓
```

Это не обязательный gate SSAD. Это способ быстро увидеть незакрытые области знания.

## Ошибка: validation как чтение документа

Плохо:

```text
"Посмотрите спецификацию, если всё нормально — поставьте плюс."
```

Лучше:

```text
QA
→ проверьте переходы suspended → active и edge cases

Backend developer
→ проверьте возможность реализации reconciliation

Integration owner
→ подтвердите semantics webhook payload
```

Чем точнее вопрос, тем выше качество validation.

> **SSAD валидирует не текст. SSAD валидирует утверждения о системе.**
