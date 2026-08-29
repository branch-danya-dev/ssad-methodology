# Change Surface

Initial Scope показывает, **с чего начинается изменение**.

Change Surface показывает:

> **Какие части системы и знания реально могут быть затронуты этим изменением?**

## Идея

Change Surface — это не список всех связанных документов и не dependency dump.

Это карта затронутых областей ответственности и типов знания.

```text
INITIAL SCOPE
    ↓
AFFECTED RESPONSIBILITIES
    ↓
AFFECTED OWNERS
    ↓
LOCAL MODELS
    ↓
INTERFACES / INTEGRATIONS
    ↓
FLOWS / TRUST / FAILURES
    ↓
CHANGE SURFACE
```

## Что искать

Для каждой потенциально затронутой responsibility zone проверяйте:

```text
Behavior
States
Data
Interfaces
Integrations
Flows
Trust
Failures
Invariants
```

Не каждый аспект обязательно изменится. Но каждый релевантный аспект должен быть проверен.

## Метод

### 1. Начать с primary responsibility

Где находится канонический владелец изменяемого решения или состояния?

### 2. Пройти по исходящим контрактам

Кто потребляет изменяемое знание или поведение?

### 3. Пройти по входящим зависимостям

Какие факты и решения нужны primary owner для работы?

### 4. Проверить сквозные flows

Какие сценарии проходят через затронутую область?

### 5. Проверить trust и failures

Изменение normal path может неожиданно изменить degraded path, retry или offline behavior.

### 6. Отделить direct impact от potential impact

Полезно явно маркировать:

```text
DIRECT
INDIRECT
POTENTIAL
OUT OF SCOPE
```

Это снижает ложную полноту и помогает review.

## Пример Aveli

Изменение:

> увеличить offline trust window для access.

Primary responsibility:

```text
backend/access
```

Change Surface может включать:

```text
DIRECT
- access trust policy
- token/access validity model

INDIRECT
- frontend offline decision
- logout behavior
- expiry UI

POTENTIAL
- billing reconciliation timing
- revocation behavior

OUT OF SCOPE
- local professional workspace ownership
```

Последний пункт особенно важен: изменение доступа не означает изменение ownership пользовательских данных.

## Хорошая Change Surface отвечает

```text
Что меняется напрямую?
Что зависит от изменяемого поведения?
Кто владеет этими областями?
Какие контракты пересекаются?
Какие flows проходят через них?
Какие invariants могут быть нарушены?
Какие области проверены и признаны unaffected?
```

## Ошибки

### 1. Искать только по именам файлов

Связи знания могут быть графовыми и не совпадать с физической структурой.

### 2. Считать всякую зависимость изменением

Dependency ≠ impact.

### 3. Не фиксировать unaffected areas

Тогда scope постепенно разрастается без причины.

### 4. Игнорировать failure paths

Именно там часто возникает скрытая поверхность изменения.

## Результат

Change Surface должна быть достаточно точной, чтобы определить:

- кого подключить к review;
- какие canonical knowledge areas открыть;
- что нужно проверить на совместимость;
- какие regression scenarios обязательны.

Далее: [`../compatibility-risk/`](../compatibility-risk/).
