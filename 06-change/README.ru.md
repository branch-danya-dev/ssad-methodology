# 06 · Change

Этот раздел посвящён анализу изменений в существующей системе.

## Главный вопрос

> **Что реально затронет изменение, какие утверждения о системе могут перестать быть истинными и что нужно проверить заново?**

Изменение существующей системы отличается от анализа «с нуля»: большая часть знаний уже существует и считается стабильной.

Поэтому задача аналитика — не повторить полный анализ, а **точно определить область воздействия изменения и переоткрыть только необходимые знания**.

## Базовая модель

```text
CHANGE REQUEST
      ↓
INITIAL SCOPE
что должно измениться в наблюдаемом поведении?
      ↓
CHANGE SURFACE
какие responsibilities, owners и knowledge areas затронуты?
      ↓
COMPATIBILITY & RISK
что может перестать работать или быть истинным?
      ↓
SELECTIVE REOPENING
какие стабильные утверждения нужно проверить заново?
      ↓
REVIEW / IMPLEMENTATION / VERIFICATION
появляется новое evidence
      ↓
STABILIZATION
каноническое знание снова соответствует реальной системе
```

## Темы раздела

### [`initial-scope/`](initial-scope/)

Отделить цель изменения от предложенного технического решения и сформировать стартовую гипотезу scope.

### [`change-surface/`](change-surface/)

Пройти от primary responsibility через owners, contracts, flows, trust и failures и определить реальную поверхность воздействия.

### [`compatibility-risk/`](compatibility-risk/)

Проверить обратную совместимость поведения, состояний, данных, контрактов и integrations, а также rollout, migration и rollback.

### [`selective-reopening/`](selective-reopening/)

Переоткрыть только те canonical claims, которые могли перестать быть истинными, и стабилизировать их после получения нового evidence.

## Change не заменяет Workflow

`06-change` не является отдельным delivery process.

Обычный рабочий цикл из [`02-workflow/`](../02-workflow/) остаётся тем же:

```text
Pre-analysis
→ Requirements
→ Analysis & Design
→ Specification
→ Review
→ Grooming
→ Delivery Support
→ Verification
→ Knowledge Update
```

Change analysis — это **сквозная механика**, которая помогает понять, какие части уже существующей модели нужно открыть внутри этого workflow.

## Связь с Analysis

Change Surface использует аналитические перспективы из [`03-analysis/`](../03-analysis/):

```text
Boundaries
Responsibilities
Ownership
Behavior
States
Data
Interfaces
Integrations
Flows
Trust
Failures
Synthesis
```

Но вопрос теперь другой.

При первичном анализе:

> Как устроена система?

При изменении:

> Какие из уже известных утверждений о системе перестанут быть истинными, если мы внесём это изменение?

## Связь с Knowledge Structure

Через [`04-knowledge-structure/`](../04-knowledge-structure/) Change Surface связывается с каноническими владельцами знания.

```text
Affected system area
        ↓
Affected claim
        ↓
Canonical owner
        ↓
Selective reopening
```

Именно поэтому SSAD не рекомендует начинать изменение с массового редактирования связанных документов.

## Связь с Collaboration

Через [`05-collaboration/`](../05-collaboration/) определяется, кто должен участвовать в повторной validation:

- business / product — изменилось ли требуемое поведение;
- architect — допустимы ли новые зависимости и границы;
- developer — совместимо ли решение с реализацией;
- QA — какие regression и edge cases нужно перепроверить;
- integration owner — сохраняется ли внешний контракт;
- operations/security — меняются ли operational и trust assumptions.

## Принцип unaffected knowledge

Очень важно не только определить affected areas, но и явно остановить распространение scope.

```text
DIRECT
INDIRECT
POTENTIAL
OUT OF SCOPE
```

`OUT OF SCOPE` — не отсутствие анализа. Это результат проверки, что конкретная область не требует переоткрытия.

## Пример Aveli

Предположим, нужно увеличить offline trust window доступа.

```text
Initial Scope
→ пользователь дольше сохраняет ограниченный offline access

Change Surface
→ access policy
→ client offline decision
→ reconciliation
→ revocation / expiry behavior

Compatibility & Risk
→ stale access
→ backend/frontend state divergence
→ reconnect requirements

Selective Reopening
→ trust policy
→ access state model
→ degraded flow
→ reconciliation assumptions

Unaffected
→ ownership локального professional workspace
```

Так изменение одного параметра рассматривается через системные последствия, но не заставляет повторно анализировать несвязанные области.

## Проверка качества change analysis

Перед реализацией должно быть возможно ответить:

```text
Что именно меняется?
Что должно остаться неизменным?
Какие responsibilities затронуты?
Какие canonical owners нужно подключить?
Какие contracts / data / states / flows затронуты?
Что может сломаться для старых consumers или данных?
Какие invariants нужно защитить?
Как выглядит rollout / migration / rollback?
Какие знания переоткрыты?
Какие области проверены и признаны unaffected?
Как новое evidence вернётся в canonical knowledge?
```

## Главный принцип

> **Изменение не открывает всю документацию. Оно открывает только те утверждения о системе, которые могли перестать быть истинными.**

Следующий раздел: [`07-practice/`](../07-practice/).
