# API / contract checklist

Короткий маршрут для ситуации: **«Нужно спроектировать или проверить API/контракт.»**

## 1. Сначала семантика, потом JSON

- Какую ответственность выражает операция?
- Кто инициатор?
- Какой результат он запрашивает?
- Кто владеет изменяемым состоянием?
- Что операция обещает вызывающей стороне?

## 2. Resource / command semantics

- Это чтение состояния, команда или событие?
- Как идентифицируется ресурс?
- Какие переходы состояния допустимы?
- Что означает повторный вызов?

## 3. Request

- Какие поля обязательны?
- Откуда берётся каждое поле?
- Кто владеет их смыслом?
- Какие validation rules действуют?
- Есть ли correlation/idempotency key?

## 4. Response

- Что означает success?
- Возвращается authoritative state или только подтверждение приёма?
- Какие поля nullable/optional и почему?
- Какие ошибки различимы для клиента?

## 5. Error semantics

Не ограничивайся кодами `400/404/500`.

Для значимой ошибки определи:

```text
Condition
Meaning
HTTP / protocol status
Machine-readable code
Client reaction
Retryability
Resulting state
```

## 6. Compatibility

- Как версионируется контракт?
- Можно ли добавить поле без поломки старых клиентов?
- Можно ли удалить/переименовать поле?
- Возможны ли mixed versions во время rollout?

## Минимальный результат

```text
Purpose
Owner
Operation semantics
Request contract
Response contract
Errors
State effects
Idempotency
Compatibility rules
Examples
```

## Куда идти дальше

- [`03-analysis/interfaces`](../../03-analysis/interfaces/)
- [`03-analysis/behavior`](../../03-analysis/behavior/)
- [`03-analysis/states`](../../03-analysis/states/)
- [`06-change/compatibility-risk`](../../06-change/compatibility-risk/)
