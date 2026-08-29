# Trust

Trust в SSAD — это не абстрактное свойство безопасности. Это явное решение системы о том, **каким данным, состояниям и решениям можно доверять, в каких пределах и на какой срок**.

## Главный вопрос

> Почему эта зона системы имеет право использовать это значение или решение как достаточно надёжное?

## Где появляется trust

Trust возникает всякий раз, когда одна зона использует информацию, которой владеет или которую произвела другая сторона.

Примеры:

- frontend использует access state от backend;
- backend принимает purchase evidence от RevenueCat;
- offline client продолжает использовать последнее подтверждённое состояние;
- сервис принимает identity claims из токена;
- система использует данные из кэша.

## Базовая модель

```text
Source
  ↓ evidence/state
Consumer
  ↓ trust rule
Allowed decision or behavior
```

Но trust всегда должен быть ограничен.

```text
Trusted for what?
Trusted by whom?
Trusted for how long?
Under which conditions?
How is trust revoked or refreshed?
```

## Trust != ownership

Зона может доверять чужому состоянию, но не владеть им.

Например:

```text
Backend owns effective access.
Frontend trusts backend access state for rendering UI.
```

Frontend не становится владельцем access только потому, что использует его локально.

## Trust != freshness

Данные могут быть достоверными в момент получения, но устаревшими позже.

Поэтому полезно анализировать:

```text
authority
freshness
validity window
revocation
revalidation
```

## Пример: bounded offline trust

Aveli может позволять пользователю временно продолжать работу без сети на основании последнего подтверждённого access state.

Это не означает бесконечное доверие.

```text
Backend confirms access
        ↓
Client stores trusted snapshot
        ↓
Offline period
        ↓
Trust remains valid only inside bounded window
        ↓
Revalidation required
```

Ключевая идея:

> Offline behavior должен быть следствием явной trust policy, а не случайным эффектом кэша.

## Что нужно определить

Для каждого trust relationship ответьте:

- кто является authority;
- кто consumer;
- какое значение/решение используется;
- для каких действий оно достаточно;
- как долго оно считается допустимым;
- как определяется устаревание;
- как trust обновляется;
- как trust отзывается;
- что происходит, если revalidation невозможна.

## Метод анализа

```text
1. Найдите место, где зона использует чужое состояние/решение.
2. Определите authority источника.
3. Определите scope доверия.
4. Определите validity window.
5. Определите refresh/revalidation.
6. Определите revocation.
7. Опишите поведение при невозможности подтвердить доверие.
```

## Результат

Хорошая trust-модель позволяет объяснить:

```text
кто кому доверяет;
чему именно;
на каком основании;
в каких пределах;
как долго;
как это доверие прекращается.
```

## Типичные ошибки

### Считать кэш доверенным бесконечно

Cached state требует правил freshness и revalidation.

### Путать trust и ownership

Consumer не становится authority только потому, что использует значение.

### Не описывать revoke path

Если trust можно выдать, должен быть понятен механизм его прекращения.

### Считать offline отдельным режимом без правил

Offline behavior должен следовать из trust policy и ownership model.

## Проверка

Trust описан достаточно хорошо, если команда может ответить:

- кто authority;
- какой consumer использует состояние;
- для каких решений это допустимо;
- когда состояние перестаёт считаться надёжным;
- что происходит при невозможности revalidation.

Следующая перспектива: [`../failures/`](../failures/).
