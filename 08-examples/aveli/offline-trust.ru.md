# Aveli · bounded offline trust

## Системный вопрос

Как позволить пользователю продолжать профессиональную работу без постоянной сети, не превращая локальный клиент в постоянный источник истины о праве доступа?

## SSAD-мышление

Offline behavior — это не просто «если нет сети, показать кэш».

Нужно явно определить:

```text
что именно сохраняется локально;
почему этому можно доверять;
как долго действует доверие;
что происходит после истечения срока;
что происходит с пользовательскими данными;
как система восстанавливается после появления сети.
```

## Aveli

Профессиональное рабочее пространство хранится локально и не требует постоянной доступности backend для обычной работы.

При этом решение о праве доступа остаётся серверной ответственностью.

Клиент может сохранять ранее проверенный `AccessState` в защищённом хранилище.

```text
Backend доступен
→ получить проверенный AccessState
→ сохранить trusted snapshot

Backend / сеть недоступны
→ проверить допустимость snapshot
→ временно продолжить работу либо потребовать сеть
```

## Trust window

У доверенного снимка нет бесконечного срока жизни.

Если сервер возвращает `nextVerificationRequiredAt`, этот срок определяет следующую обязательную проверку.

В текущей реализации также существует fallback-период, когда явный серверный срок отсутствует и политика допускает это поведение.

Важно: конкретное fallback-значение является implementation detail, а не вечной бизнес-константой.

## Критический инвариант

```text
network unavailable
≠
workspace deleted

access verification expired
≠
workspace deleted
```

Истечение доверия к access snapshot меняет доступность функции, но не ownership и lifecycle профессиональных данных.

Это предотвращает опасное смешение двух независимых вопросов:

```text
Могу ли я сейчас открыть workspace?

и

Существуют ли мои локальные профессиональные данные?
```

## Failure и recovery

При восстановлении сети повторная проверка может выполняться через:

```text
user retry
app resume
billing reconciliation
access refresh
```

Таким образом offline policy включает не только happy path, но и:

```text
trust source
validity window
expiration behavior
failure state
recovery path
```

## Канонический источник Aveli

https://github.com/branch-danya-dev/aveli-system-analysis/blob/main/system/flows/offline-workspace.ru.md

Локальные детали принадлежат соответствующим frontend/backend областям, а сквозной инвариант фиксируется на system level.

## Связь с SSAD

- [`../../03-analysis/trust/README.ru.md`](../../03-analysis/trust/README.ru.md)
- [`../../03-analysis/failures/README.ru.md`](../../03-analysis/failures/README.ru.md)
- [`../../03-analysis/states/README.ru.md`](../../03-analysis/states/README.ru.md)
- [`../../03-analysis/synthesis/README.ru.md`](../../03-analysis/synthesis/README.ru.md)

## Что показывает весь кейс Aveli

Три среза вместе дают один путь:

```text
SYSTEM STRUCTURE
↓
CANONICAL OWNERSHIP
↓
CROSS-BOUNDARY FLOW
↓
TRUST & FAILURE POLICY
↓
SYSTEM SYNTHESIS
```

Это и есть главный смысл examples в SSAD: не дать ещё один шаблон, а показать, как аналитические принципы работают на реальной системе.
