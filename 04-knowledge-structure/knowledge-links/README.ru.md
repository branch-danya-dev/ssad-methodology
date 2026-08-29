# Knowledge Links

Иерархия определяет, **где знание живёт**. Ссылки показывают, **с чем оно связано**.

## Проблема

Реальная система не является деревом. Один flow может связывать frontend, backend, billing, access, интеграцию и локальное состояние устройства.

Если пытаться физически положить всё связанное знание в одну директорию, структура быстро начинает дублировать факты или смешивать ответственности.

## Принцип

```text
PHYSICAL STORAGE = HIERARCHY
KNOWLEDGE RELATIONSHIPS = GRAPH
```

Документ хранится у своего канонического владельца, но может иметь ссылки на:

- входящие и исходящие интерфейсы;
- зависимые правила;
- связанные состояния;
- сквозные flows;
- решения;
- внешние интеграции;
- verification evidence.

## Ссылка должна объяснять отношение

Плохая ссылка:

```text
See billing.md
```

Хорошая ссылка:

```text
Access does not derive subscription truth locally.
It consumes the reconciled entitlement state owned by Billing.
See: ../billing/entitlement.md
```

Ссылка переносит не только пользователя, но и смысл зависимости.

## Контекст вместо копии

Если локальному документу нужен чужой факт, достаточно:

```text
local context
+
relationship explanation
+
canonical link
```

Не нужно копировать весь чужой раздел.

## Граф помогает change analysis

Связи позволяют проследить область влияния изменения:

```text
changed rule
↓
canonical owner
↓
consumers
↓
interfaces / flows / tests
↓
change surface
```

Поэтому ссылки — не украшение навигации, а часть модели зависимостей системного знания.

Следующая тема: [`../progressive-depth/`](../progressive-depth/).
