# Semantic Reference · смысл до API representation

[English version](semantic-reference.md)

## Проблема

Для создания размеров Revit требует технические `Reference`, которые принимает host API.

Но аналитический вопрос должен быть первым:

> **Какой structural fact этот размер должен сообщать?**

Если начать проектирование с API objects, технически удобный reference может незаметно переопределить intended system meaning.

## Два слоя

```text
SEMANTIC TARGET
что должно быть размерено?

        ↓ realization

REVIT REFERENCE
как представить этот target для NewDimension?
```

Примеры semantic targets:

- left/right boundaries нормализованной reinforcement zone;
- ближайшая валидная structural grid слева;
- ближайшая валидная grid справа;
- ближайшие валидные grid above/below.

Revit `Reference` — только host-compatible representation одного из этих targets.

## Direction раньше distance

Grid selection хорошо показывает, почему semantic rules должны существовать независимо от API representation.

```text
          Above
            ↑
            │
Left ← [ Zone ] → Right
            │
            ↓
          Below
```

Для left-grid dimension допустимы только grid слева.

```text
closer grid on wrong side
!= valid semantic target
```

Host API вполне может позволить построить размер к неправильной оси. Это не делает результат корректным.

## Supporting geometry как adaptation

Raw boundaries `Area Reinforcement` не всегда дают stable references, подходящие для dimension creation в Revit.

Поэтому plugin может создавать supporting detail geometry:

```text
canonical zone boundary intent
        ↓
Revit representation limitation
        ↓
supporting detail curve
        ↓
usable Reference
        ↓
native Dimension
```

Detail curve не становится новым источником геометрической истины.

Это **adapter между system meaning и host representation**.

Различие важно, потому что implementation workarounds легко превращаются в случайную архитектуру, если их роль не описана явно.

## Optionality против failure

SSAD migration обнаружила два состояния, которые в простой модели “dimension created / not created” выглядели одинаково.

### Semantic target отсутствует

Например, справа от зоны нет structural grid.

```text
right grid target
→ NOT APPLICABLE
→ right-grid dimension не требуется
```

### Semantic target есть, но realization не удалась

Например, валидная grid/boundary существует, но Revit отвергает reference combination.

```text
semantic target exists
+
valid dimension intent exists
+
host realization fails
        ↓
FAILED WRITE / REFERENCE REALIZATION
```

Эти outcomes нельзя смешивать.

```text
NOT REQUIRED
!=
FAILED TO REALIZE
```

Первое — корректное поведение системы. Второе — failure evidence.

## Ownership model

```text
Geometry
→ владеет zone boundaries

References
→ владеет semantic reference selection

Layout
→ владеет dimension intent и placement

Revit Boundary
→ владеет host-valid realization constraints

Annotations
→ владеет generated native result
```

Ни одна responsibility не обязана владеть всей цепочкой.

Система возникает из связи владельцев.

## Общий вывод для SSAD

Та же модель работает далеко за пределами Revit:

```text
business/system meaning
!=
wire representation
!=
database representation
!=
framework object
```

OpenAPI DTO, SQL row, Kafka message, SDK object и Revit `Reference` могут представлять системный смысл, не владея им.

> **Сначала выбери semantic target. Затем выбери техническое representation, которое сохраняет его смысл.**

Каноническое проектное знание:
https://github.com/branch-danya-dev/revit-rebar-autodim-analysis/tree/main/references

Далее: [`Generated Output Ownership`](generated-output-ownership.ru.md)
