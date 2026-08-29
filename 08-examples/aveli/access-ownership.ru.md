# Aveli · ownership доступа и биллинга

## Системный вопрос

Кто в системе имеет право окончательно решить, что пользователь может открыть профессиональное рабочее пространство?

Наивный ответ:

```text
RevenueCat сообщает активную подписку
→ значит RevenueCat управляет доступом
```

Для SSAD этого недостаточно.

## Разделяем evidence и authority

В Aveli внешний биллинг и внутренний доступ — разные ответственности.

```text
Store / RevenueCat
→ подтверждают состояние биллинга провайдера

Aveli Backend
→ принимает итоговое решение о доступе к рабочему пространству
```

RevenueCat является важным источником evidence, но не владельцем продуктового решения Aveli.

## Сквозной сценарий

```text
Покупка в магазине
        ↓
RevenueCat CustomerInfo
        ↓
Flutter
        ↓
POST /v1/billing/sync
        ↓
Aveli Backend
        ↓
проверка состояния через RevenueCat
        ↓
нормализация subscription state
        ↓
расчёт AccessStatus
        ↓
Frontend
```

Есть и асинхронный путь:

```text
RevenueCat webhook
→ Aveli Backend
→ idempotency check
→ RevenueCat reconciliation
→ subscription snapshot
→ access evaluation
```

Тип webhook-события сам по себе не выдаёт и не отзывает доступ.

## Почему ownership нельзя вывести из потока данных

Данные проходят через несколько систем:

```text
Store
→ RevenueCat
→ Backend
→ Frontend
```

Но направление потока не отвечает на вопрос authority.

SSAD отдельно спрашивает:

```text
Кто предоставляет evidence?
Кто хранит каноническое нормализованное состояние?
Кто принимает итоговое решение?
Кто только потребляет результат?
```

Для Aveli:

```text
billing evidence
→ Store / RevenueCat

normalized billing state
→ Backend

workspace access decision
→ Backend

access consumer
→ Frontend
```

## Важный системный инвариант

Подписка — не единственный возможный источник доступа.

Общая модель может учитывать:

```text
permanent access
manual entitlement
subscription
trial
```

Поэтому нельзя заменить внутреннюю access model простым вопросом «активна ли подписка RevenueCat?».

## Канонические источники Aveli

Сквозной сценарий:

https://github.com/branch-danya-dev/aveli-system-analysis/blob/main/system/flows/purchase-and-entitlement.ru.md

Локальное знание распределено между:

```text
integrations/revenuecat/
backend/billing/
system/flows/
```

Это хороший пример принципа:

> **Хранение иерархично. Знание связано графом.**

## Связь с SSAD

- [`../../03-analysis/ownership/README.ru.md`](../../03-analysis/ownership/README.ru.md)
- [`../../03-analysis/integrations/README.ru.md`](../../03-analysis/integrations/README.ru.md)
- [`../../03-analysis/flows/README.ru.md`](../../03-analysis/flows/README.ru.md)
- [`../../03-analysis/synthesis/README.ru.md`](../../03-analysis/synthesis/README.ru.md)

Далее: [`offline-trust.ru.md`](offline-trust.ru.md)
