# Integration checklist

Короткий маршрут для ситуации: **«Нужно проанализировать новую или изменяемую интеграцию.»**

## 1. Граница

- Какая система внешняя относительно нашей?
- Где проходит ownership boundary?
- Кто владеет контрактом с каждой стороны?

## 2. Цель взаимодействия

- Зачем интеграция существует?
- Что инициирует обмен?
- Какой бизнес- или системный результат должен возникнуть?

## 3. Контракт

- Какой transport/protocol используется?
- Какие request/event fields обязательны?
- Что означает каждый значимый field?
- Какие ответы, статусы и ошибки возможны?
- Есть ли versioning и backward compatibility?

## 4. Ownership и authority

- Кто владеет передаваемыми данными?
- Получаем мы факт, evidence или authoritative decision?
- Может ли наша система изменить полученное состояние?
- Требуется ли reconciliation?

## 5. Время и повторная доставка

- Синхронное или асинхронное взаимодействие?
- Возможны ли duplicate/out-of-order события?
- Что происходит при timeout?
- Есть ли retry, idempotency, deduplication?

## 6. Failure behavior

- Что произойдёт, если внешняя система недоступна?
- Какое состояние остаётся у нашей системы?
- Можно ли продолжать работу в degraded mode?
- Как происходит recovery после восстановления связи?

## 7. Trust

- Почему мы доверяем источнику?
- Как проверяется подлинность сообщения/ответа?
- Сколько времени полученная информация считается валидной?
- Что происходит при revocation или конфликтующем evidence?

## Минимальный результат

```text
Integration purpose
Ownership boundary
Contract semantics
Data / decision ownership
Trigger and flow position
Retry / idempotency rules
Failure behavior
Trust assumptions
Reconciliation rules
Open questions
```

## Куда идти дальше

- [`03-analysis/integrations`](../../03-analysis/integrations/)
- [`03-analysis/interfaces`](../../03-analysis/interfaces/)
- [`03-analysis/trust`](../../03-analysis/trust/)
- [`03-analysis/failures`](../../03-analysis/failures/)
