# Enterprise Workplace Migration · real-world application SSAD

[English version](README.md)

Этот application показывает, как SSAD ведёт себя на системе, которая существенно отличается от обычного software product.

Полный реконструированный кейс:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

Кейс — это санитизированная реконструкция масштабной enterprise-миграции рабочих мест с Microsoft Windows на Astra Linux в банковской среде.

Он моделируется не как «установка операционной системы».

Объект анализа — **управляемое изменение рабочего места сотрудника с сохранением способности выполнять требуемую бизнес-деятельность**.

## Почему этот кейс важен для SSAD

Aveli помог проверить SSAD на product-shaped системе с frontend, backend, локальными данными, billing, trust и integrations.

Enterprise Workplace Migration проверяет совершенно другую форму системы:

- нет одного application boundary, внутри которого находится вся система;
- evidence распределён между несколькими support- и infrastructure-доменами;
- readiness — cross-team решение, а не свойство одного компонента;
- planning и фактическое execution имеют независимую историю;
- failures создают явные operational recovery paths;
- одно рабочее место одновременно может иметь разные readiness, planning, execution и exception states;
- API/database артефакты являются только synthetic projections реконструированного домена.

Поэтому кейс проверяет, умеет ли SSAD обобщаться за пределы той формы системы, которая помогала методологию создавать.

## Что изменилось после применения SSAD

Изначальный portfolio-репозиторий был организован по типам артефактов:

```text
docs/
api/
sql/
diagrams/
```

После применения SSAD активное знание организовано по системным responsibility areas:

```text
system/
workplace/
readiness/
planning/
execution/
exceptions/
integrations/
technical-projection/
```

Главный результат — не переименование директорий. Изменилась сама модель анализа.

Например, прежний общий migration status:

```text
Scheduled
Ready
Postponed
Blocked
Migration In Progress
Manual Migration Required
Dual Boot
Migrated
```

был разложен на независимые dimensions с отдельным ownership.

## Структура application

```text
1. Responsibility Structure
   ↓
почему migration programme требует других owners, чем product system

2. Global Status Decomposition
   ↓
почему один migration_status скрывал несколько независимых state models

3. Evidence and Readiness
   ↓
почему distributed evidence не означает distributed system meaning

4. Technical Projection
   ↓
как исправленная domain model изменила REST и relational design
```

Вместе они показывают:

```text
SYSTEM BOUNDARY
↓
RESPONSIBILITY MODEL
↓
OWNERSHIP
↓
INDEPENDENT STATES
↓
CROSS-BOUNDARY EVIDENCE
↓
TECHNICAL PROJECTION
↓
SYSTEM SYNTHESIS
```

## Как читать application

Каждый срез отвечает на четыре вопроса:

```text
Что было сложным в исходном кейсе?
Что SSAD заставила разделить?
Что изменилось в итоговой модели?
Где живёт каноническая проектная истина?
```

Application намеренно не копирует полный enterprise-репозиторий.

> **SSAD объясняет ход анализа. Каноническая проектная истина остаётся в проектном репозитории.**

Начать: [`responsibility-structure.ru.md`](responsibility-structure.ru.md)
