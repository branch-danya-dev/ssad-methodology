# Compatibility & Risk

Change Surface отвечает на вопрос **что может быть затронуто**.

Compatibility & Risk отвечает:

> **Какие существующие ожидания, контракты и инварианты могут перестать быть истинными после изменения?**

## Проблема

Изменение может быть локальным по реализации и глобальным по последствиям.

Например:

```text
добавить обязательное поле
изменить enum
переименовать статус
увеличить trust window
сменить источник истины
изменить порядок событий
```

Каждое из них может нарушить существующих потребителей, данные, migrations, retries или пользовательские сценарии.

## Аналитические слои совместимости

Проверяйте как минимум:

```text
Behavior compatibility
State compatibility
Data compatibility
Contract compatibility
Integration compatibility
Operational compatibility
Trust compatibility
```

## Контракты

Для каждого изменяемого интерфейса спросите:

```text
Старый consumer продолжит работать?
Новый producer понятен старому consumer?
Меняется обязательность полей?
Меняется семантика без изменения формы?
Меняется порядок событий?
Есть ли versioning strategy?
```

Семантическая несовместимость часто опаснее синтаксической.

## Данные и migration

```text
Как выглядят существующие данные?
Можно ли прочитать их новой логикой?
Нужно ли преобразование?
Можно ли откатиться после migration?
Как жить во время смешанного состояния версий?
```

## States

Изменение state model требует проверить:

- старые состояния;
- новые состояния;
- допустимые переходы;
- зависшие/legacy состояния;
- переход в rollback-сценарии.

## Rollout compatibility

В распределённой системе компоненты редко обновляются одновременно.

Поэтому полезно моделировать:

```text
OLD producer → OLD consumer
NEW producer → OLD consumer
OLD producer → NEW consumer
NEW producer → NEW consumer
```

Не все комбинации обязаны поддерживаться, но решение должно быть явным.

## Risk model

SSAD не требует сложной числовой модели риска.

Практически достаточно оценить:

```text
Likelihood
Impact
Detectability
Recoverability
```

Особенно важна recoverability: одинаковая вероятность сбоя имеет разный риск, если один случай откатывается за минуту, а другой необратимо портит данные.

## Пример Aveli

Изменение:

> увеличить offline access trust window с короткого периода до нескольких дней.

Риски:

```text
Trust compatibility
→ отозванная подписка может дольше считаться активной локально

State compatibility
→ frontend и backend могут дольше расходиться по access state

Failure behavior
→ reconnect/reconciliation становится критичнее

Operational risk
→ потребуется наблюдаемость stale access decisions
```

То есть изменение одной policy меняет не только число в конфигурации.

## Rollback

Rollback нужно анализировать до реализации.

```text
Можно ли вернуть старую версию кода?
Поймёт ли она новые данные?
Можно ли отменить migration?
Что делать с уже выданными новыми состояниями/токенами?
Нужно ли forward-fix вместо rollback?
```

## Результат

После анализа compatibility & risk должно быть понятно:

- какие ожидания могут сломаться;
- какие consumers и данные требуют защиты;
- нужен ли versioning/migration;
- как выполнять rollout;
- как проверять mixed-version period;
- возможен ли rollback;
- какие риски требуют отдельного review или mitigation.

## Проверка

```text
[ ] проверена семантика изменяемых контрактов
[ ] проверены существующие данные
[ ] рассмотрены старые состояния
[ ] рассмотрены mixed-version сценарии
[ ] определены critical invariants
[ ] понятен rollout
[ ] понятен rollback или forward-fix strategy
[ ] ключевые риски имеют mitigation / detection
```

Далее: [`../selective-reopening/`](../selective-reopening/).
