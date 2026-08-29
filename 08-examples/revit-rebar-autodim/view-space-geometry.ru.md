# View-Space Geometry · контекст меняет смысл

[English version](view-space-geometry.md)

## Проблема

Rebar AutoDim размеряет геометрию, которая уже существует в модели Revit, но annotation meaning нельзя напрямую получить из глобальных project X/Y axes.

Для этой системы:

```text
model geometry
+
active view orientation
        ↓
annotation geometry meaning
```

Одна и та же structural geometry может отображаться в разных ориентациях. Поэтому width, height, left, right, above, below и dimension placement должны интерпретироваться в frame текущего вида.

## Разделение ownership

Revit владеет source geometry.

Active view владеет contextual frame, используемым для annotation interpretation.

Rebar AutoDim владеет normalized representation, полученным из этих двух входов.

```text
Revit structural geometry
        ↓ evidence

Active view
→ Origin
→ RightDirection
→ UpDirection
→ ViewDirection
→ scale
        ↓ context

Rebar AutoDim Geometry
→ ZoneGeometry
```

Ни один из этих входов сам по себе не владеет итоговым annotation meaning.

## Нормализованная локальная модель

Плагин проецирует source points в view-local coordinate system:

```text
u → горизонталь вида
v → вертикаль вида
w → глубина относительно view plane
```

После этого строится локальная модель:

```text
ZoneGeometry
├── Left
├── Right
├── Bottom
├── Top
├── Width
├── Height
└── Center
```

Это хороший пример local modeling в SSAD:

> **Локальная модель может быть канонической для одной responsibility, даже если каждый исходный факт приходит от внешнего владельца.**

`ZoneGeometry` не заменяет геометрию Revit. Это каноническая интерпретация, которой plugin владеет для своей annotation responsibility.

## Иерархия evidence

Предпочтительным evidence является фактическая граница reinforcement zone.

Поддерживаемый view-specific fallback допустим только тогда, когда он сохраняет требуемый прямоугольный смысл.

```text
boundary evidence доступно?
        ↓ да
normalize

        ↓ нет
supported fallback надёжен?
        ↓ да             ↓ нет
normalize               skip
```

Fallback не даёт права изобретать прямоугольник только потому, что размер был бы полезен.

Это напрямую связано с принципом SSAD:

```text
insufficient evidence
!= permission to manufacture certainty
```

## Контекст участвует в Change analysis

Source reinforcement zone может не измениться, а execution context — измениться.

Например:

- другой active view;
- изменённая ориентация вида;
- изменённый scale;
- изменённый crop region;
- изменённая visibility.

Поэтому предыдущая annotation interpretation может перестать быть актуальной, даже если сам structural element не менялся.

```text
source unchanged
+
context changed
        ↓
reopen geometry/layout interpretation
```

Это хороший пример Change Surface: изменение контекста способно переоткрыть derived knowledge без изменения source entity.

## Почему это важно для SSAD

Во многих системах смысл является contextual, а не intrinsic:

```text
raw fact
+
interpretation context
→ system meaning
```

Rebar AutoDim показывает, что ownership в SSAD не должен заставлять складывать весь смысл в source-data owner.

Правильные вопросы:

```text
Кто владеет source fact?
Кто владеет context?
Кто владеет derived interpretation?
Когда эту интерпретацию нужно переоткрывать?
```

## Методологический вывод

> **Canonical knowledge может быть derived knowledge. Важно явно определить владельца интерпретации и условия её валидности.**

Каноническое проектное знание:
https://github.com/branch-danya-dev/revit-rebar-autodim-analysis/tree/main/geometry

Далее: [`Semantic Reference`](semantic-reference.ru.md)
