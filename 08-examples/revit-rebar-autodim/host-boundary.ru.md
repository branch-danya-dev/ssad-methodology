# Host Boundary · authority Revit и ответственность плагина

[English version](host-boundary.md)

## Проблема

Rebar AutoDim работает **внутри Autodesk Revit**. Поэтому system boundary здесь необычная.

Плагин не владеет документом, видом, structural geometry, native references или transaction engine. Но при этом он обязан принимать собственные системные решения о том, как эти факты интерпретируются для задачи размерения армирования.

Если смешать эти зоны, поведение host API начинает выглядеть как бизнес-/системная модель самого плагина.

## Граница

```text
AUTODESK REVIT
владеет
- document and view state
- source geometry Area Reinforcement
- geometry/references structural grids
- native element validity
- transaction semantics

             boundary
                ↓

REBAR AUTODIM
владеет
- supported execution interpretation
- normalized zone meaning
- dimension/reference intent
- placement policy
- generated annotation result
- regeneration ownership
```

Плагин потребляет Revit evidence и capabilities. Чтение факта не передаёт ownership этого факта плагину.

## Асимметрия read/write

Плагин читает structural truth, но пишет только в собственный annotation layer.

```text
SOURCE MODEL
Area Reinforcement
Structural Grids
View Context
      ↓ read

REBAR AUTODIM
      ↓ write

PLUGIN-OWNED OUTPUT
Detail Curves
Dimensions
Generation Metadata
```

Это более содержательная граница, чем просто «использует Revit API».

Инвариант:

> **Удобство аннотирования не даёт права менять structural source truth.**

## Host authority не означает ownership решения

Revit определяет, является ли конкретный `Reference`, line, element creation или transaction технически валидным.

Rebar AutoDim определяет, представляет ли этот технический объект правильный annotation meaning.

```text
Revit говорит:
“Этот Reference валиден для NewDimension.”

Rebar AutoDim всё ещё должен ответить:
“Это правильный structural target для нужного размера?”
```

Технически успешный API call всё ещё может реализовать неверный системный смысл.

## Transaction boundary как системная граница

Историческая реализация использовала отдельную transaction для каждой поддерживаемой reinforcement zone.

SSAD даёт этому implementation choice системное объяснение:

```text
one source zone
→ one independently meaningful annotation result
→ one regeneration ownership relation
→ one atomic write scope
```

Поэтому одна failed zone может откатиться, не уничтожая уже committed результаты других зон, если Revit позволяет безопасную изоляцию.

```text
Zone A → commit
Zone B → rollback
Zone C → commit
```

Transaction здесь не только Revit programming detail. Её scope выражает выбранную failure-isolation boundary.

## Что добавляет SSAD

Без явного анализа границ такую систему легко описать как:

```text
Revit API
→ collect elements
→ calculate
→ call NewDimension
→ transaction commit
```

SSAD вместо этого спрашивает:

```text
Чем владеет Revit?
Чем владеет plugin?
Какое evidence пересекает boundary?
Какие решения остаются локальными для plugin?
Какой failure scope имеет самостоятельный смысл?
```

## Методологический вывод

Внешняя зависимость не обязана быть remote service, чтобы образовывать integration/authority boundary.

Host application может быть физически ближе и обладать большей authority, чем HTTP provider, но всё равно оставаться за пределами responsibility area плагина.

> **Физическая совместность не устраняет ownership boundaries.**

Каноническое проектное знание:
https://github.com/branch-danya-dev/revit-rebar-autodim-analysis/tree/main/revit-boundary

Далее: [`View-Space Geometry`](view-space-geometry.ru.md)
