# Generated Output Ownership · source state и derived state

[English version](generated-output-ownership.md)

## Проблема

Rebar AutoDim не владеет reinforcement design, который читает из Revit.

Но он владеет другим важным состоянием: annotation result, который сам сгенерировал из source data.

Без явной ownership model повторный запуск легко превращается в накопление дублей или неоднозначное частично вручную изменённое состояние.

## Два разных state owner

```text
STRUCTURAL SOURCE STATE
Area Reinforcement
Structural Grids
        ↓ owned by Revit / structural model

DERIVED PLUGIN STATE
GeneratedAnnotationSet
Generation Metadata
        ↓ owned by Rebar AutoDim
```

Generated state сообщает факты source model, но не является самим source state.

Поэтому plugin может заменять собственный output, не претендуя на authority над reinforcement design.

## Один текущий result для source zone

Полезная ownership relation:

```text
Area Reinforcement identity
        ↓
Generation Metadata
        ↓
Current Generated Annotation Result
```

В текущей модели одна source zone должна сходиться к одному текущему plugin-owned annotation result.

Result может содержать:

- supporting detail curves;
- обязательные overall width/height dimensions;
- условные grid-offset dimensions;
- generation identity/metadata.

## Regeneration вместо patch synchronization

При rerun plugin не пытается сохранять и отдельно синхронизировать каждый generated dimension.

```text
find previous plugin-owned result
        ↓
remove previous result
        ↓
read current source/context
        ↓
recalculate
        ↓
create one new complete result
        ↓
store current ownership metadata
```

Это даёт idempotency системный смысл:

```text
unchanged source + unchanged context
Run 1 → Result A
Run 2 → replace A → Result A'

A' ≈ A по системному смыслу
```

Стабильные element IDs не обязательны. Стабильный смысл — обязателен.

## Manual edits и ownership ambiguity

Пользователь может вручную удалить или частично изменить plugin-generated elements.

Plugin не считает такие изменения новой канонической hybrid model.

```text
partial plugin-owned result
        ↓
next run
        ↓
remove remaining owned output
        ↓
regenerate from current source truth
```

Это ownership decision:

> **Пока элемент относится к plugin-owned generated set, plugin имеет право заменить его.**

Если продукт должен поддерживать долговечные user edits внутри generated output, нужно менять ownership rules, а не просто добавлять patch logic.

## Atomic replacement

Опасный outcome:

```text
old result partially deleted
+
new result partially created
```

Желаемый zone-level transition:

```text
OLD CURRENT RESULT
        ↓ transaction
NEW CURRENT RESULT
```

или при failure:

```text
OLD CURRENT RESULT
        ↓ failed transaction
OLD CURRENT RESULT remains
```

Так ownership напрямую связывается с transaction scope.

## Change analysis

Generated result может стать stale из-за изменений:

- source reinforcement geometry;
- relevant grid geometry;
- active-view context;
- dimension/reference policy;
- layout policy;
- host/API constraints.

SSAD не требует переоткрывать всё подряд.

```text
changed claim/context
        ↓
affected owners
        ↓
recalculate current generated result
```

Generated annotation set — derived state, валидность которого зависит от upstream canonical owners.

## Общий вывод для SSAD

Во многих системах есть derived/generated state:

- search indexes;
- caches;
- projections/read models;
- generated documents;
- compiled artifacts;
- local offline snapshots;
- UI-derived state.

Вопросы одинаковые:

```text
От какой source truth это зависит?
Кто владеет generated state?
Может ли пользователь менять его независимо?
Что делает его stale?
Как он пересобирается или reconciles?
Какова atomic replacement boundary?
```

> **Derived state требует явного ownership, даже если его всегда можно пересобрать.**

Каноническое проектное знание:
https://github.com/branch-danya-dev/revit-rebar-autodim-analysis/tree/main/regeneration

Вернуться к: [`Rebar AutoDim application`](README.ru.md)
