# Rebar AutoDim · host-application automation application

[English version](README.md)

Этот application показывает, как SSAD работает на **host-application automation system**, встроенной в Autodesk Revit.

Полный проектный репозиторий:

https://github.com/branch-danya-dev/revit-rebar-autodim-analysis

Rebar AutoDim автоматизирует размерение прямоугольных зон `Area Reinforcement` на активном виде Revit. Интерес для SSAD здесь не только в алгоритме размеров, а в ownership boundary между:

```text
Autodesk Revit
→ владеет model/view state, валидностью native elements,
  geometric references и transaction semantics

Rebar AutoDim
→ владеет интерпретацией этого evidence для узкой задачи,
  dimension intent, generated annotation state и regeneration rules
```

По форме эта система существенно отличается и от Aveli, и от Enterprise Workplace Migration.

## Почему этот application важен

Плагин внутри host-приложения не может считать среду выполнения своей собственной областью authority.

Нужно явно различать:

```text
host evidence
!= plugin decision

semantic target
!= host API representation

valid analysis
!= successfully committed native output

source model state
!= generated plugin-owned state
```

Эти различия проверяют, способна ли SSAD оставаться implementation-aware, не позволяя механике framework/API стать канонической моделью системы.

## Структура репозитория после применения SSAD

Проект организован вокруг устойчивых аналитических responsibility areas:

```text
system/
execution-context/
geometry/
references/
layout/
annotations/
regeneration/
revit-boundary/
evidence/
```

Это не шаблон SSAD. Такая структура появилась из реальных вопросов именно этой системы.

## Компактный маршрут application

```text
Host Boundary
      ↓
View-Space Geometry
      ↓
Semantic Reference vs API Reference
      ↓
Generated Output Ownership
```

### 1. Host Boundary

Revit одновременно является источником structural evidence и authority, определяющей, валидны ли native reference, dimension и transaction.

Rebar AutoDim владеет только своей узкой аналитической трансформацией и generated annotation layer.

→ [`Host Boundary`](host-boundary.ru.md)

### 2. View-Space Geometry

Structural model владеет геометрией, но **active view определяет annotation frame**, в котором интерпретируются width, height, left/right и placement.

Поэтому active view становится частью системного смысла, а не просто параметром API.

→ [`View-Space Geometry`](view-space-geometry.ru.md)

### 3. Semantic Reference vs API Reference

Система сначала должна решить, **что именно должно быть размерено**, и только затем определить, какой Revit `Reference` способен технически реализовать этот intent.

Supporting detail geometry поэтому является API adaptation, а не новым владельцем геометрической истины.

→ [`Semantic Reference`](semantic-reference.ru.md)

### 4. Generated Output Ownership

Исходное армирование остаётся под ownership structural model. Rebar AutoDim владеет одним текущим generated annotation result для каждой source zone и при повторном запуске заменяет его вместо накопления дублей.

→ [`Generated Output Ownership`](generated-output-ownership.ru.md)

## Что этот application подтверждает в SSAD

Кейс добавляет evidence, что SSAD умеет моделировать системы, где:

- анализируемая система работает внутри более сильной host authority;
- host владеет низкоуровневой валидностью, а plugin — domain interpretation;
- смысл геометрии зависит от execution context;
- semantic decisions требуют перевода во framework-specific representation;
- generated state имеет ownership отдельно от source state;
- transaction atomicity задаёт содержательные failure boundaries;
- implementation constraints могут требовать адаптации, не становясь владельцем системного смысла.

## Сравнение с другими real-world applications

```text
Aveli
→ product-shaped software system
→ application-owned services/data + external providers

Enterprise Workplace Migration
→ transformation-shaped enterprise system
→ distributed evidence + cross-team decisions

Rebar AutoDim
→ host-application automation system
→ external host authority + local semantic transformation
```

Общее здесь не дерево директорий.

Общее — reasoning discipline:

```text
Boundaries
→ Responsibilities
→ Ownership
→ Local models
→ Connections
→ Failures
→ Synthesis
```

## Каноническая истина

Этот каталог — validation material для методологии.

Каноническое проектное знание Rebar AutoDim остаётся в:

https://github.com/branch-danya-dev/revit-rebar-autodim-analysis

> **SSAD application объясняет, что позволила обнаружить методология. Он не становится второй спецификацией проекта.**

Вернуться к: [`08 · Examples and Applications`](../README.ru.md)
