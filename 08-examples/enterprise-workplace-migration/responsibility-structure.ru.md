# Responsibility Structure · enterprise migration

[English version](responsibility-structure.md)

## Системный вопрос

Как структурировать знание, если анализируемая система — не одно приложение, а migration programme, проходящая через рабочие места, support-домены, infrastructure tooling и operational coordination?

## Исходная сложность

Document-oriented взгляд естественно предлагает категории:

```text
requirements
business rules
API
SQL
diagrams
```

Но эти категории не отвечают на системный вопрос:

> **Кто владеет какой частью смысла миграции?**

В реальном кейсе несколько разных responsibility areas способны изменяться независимо друг от друга.

## Рассуждение по SSAD

Нужно начать с изменяемого объекта и решений вокруг него.

```text
WORKPLACE
Какое рабочее окружение существует?

READINESS
Можно ли сейчас безопасно идти по нормальному пути миграции?

PLANNING
Когда миграция должна произойти?

EXECUTION
Что фактически произошло во время попытки?

EXCEPTIONS
Что меняет нормальный путь и как выполняется recovery?

INTEGRATIONS
Какой evidence, commands и notifications пересекают внешние границы?

SYSTEM
Складываются ли локальные модели в один целостный результат миграции?
```

Итоговая структура репозитория следует этим responsibility areas:

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

Она намеренно отличается от структуры Aveli `business/backend/frontend/database/...`.

Именно это различие показывает, что SSAD не задаёт универсальное дерево директорий.

## Что стало яснее

Разделение responsibility обнаружило несколько различий, которые раньше было легко смешать:

```text
planned migration
!= actual attempt

technical attempt success
!= operational completion

readiness evidence
!= readiness authority

blocker record
!= ownership underlying technical problem

storage location
!= semantic ownership
```

Также уменьшилась область знания, которую приходится переоткрывать при изменении.

Например, изменение postponement behavior в первую очередь переоткрывает `planning/` и соответствующие integration boundaries. Оно не обязано автоматически переоткрывать workplace-state semantics или attempt history.

## Каноническая проектная истина

Полная responsibility model:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

Основные области:

- `system/`
- `workplace/`
- `readiness/`
- `planning/`
- `execution/`
- `exceptions/`
- `integrations/`

## Какие главы SSAD демонстрирует кейс

- [`03-analysis/boundaries/`](../../03-analysis/boundaries/)
- [`03-analysis/responsibilities/`](../../03-analysis/responsibilities/)
- [`03-analysis/ownership/`](../../03-analysis/ownership/)
- [`04-knowledge-structure/storage-hierarchy/`](../../04-knowledge-structure/storage-hierarchy/)
- [`04-knowledge-structure/progressive-depth/`](../../04-knowledge-structure/progressive-depth/)

Далее: [`global-status-decomposition.ru.md`](global-status-decomposition.ru.md)
