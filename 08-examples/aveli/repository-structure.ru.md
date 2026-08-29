# Aveli · структура репозитория как модель системы

## Системный вопрос

Как организовать аналитическое знание так, чтобы человеку было понятно, где искать истину о конкретной части системы?

## SSAD-мышление

SSAD не начинает с универсального дерева:

```text
requirements/
diagrams/
api/
security/
```

Сначала определяется реальная структура ответственности, а уже затем ей назначаются владельцы знания.

## Aveli

В Aveli естественными верхнеуровневыми областями стали:

```text
business/
database/
backend/
frontend/
integrations/
system/
```

Это не шаблон SSAD. Это результат анализа конкретной системы.

### Что принадлежит локальным областям

```text
business/
→ продуктовый контекст, требования и правила

backend/
→ серверное поведение, аккаунт, auth, access, billing, API

frontend/
→ Flutter-клиент, navigation, local state, offline behavior

database/
→ владение данными, модели и физическое хранение

integrations/
→ внешние ownership boundaries
```

### Зачем существует `system/`

Декомпозиции недостаточно.

Есть знание, которое не принадлежит одному компоненту:

```text
end-to-end flows
cross-component trust
system invariants
multi-component evolution
system-level review
```

Поэтому Aveli содержит `system/` как область синтеза, а не как свалку «общих документов».

## Главный урок

```text
LOCAL OWNERSHIP
→ уменьшает область чтения

SYSTEM SYNTHESIS
→ не даёт локально правильным описаниям противоречить друг другу
```

Именно поэтому тезис «структурируй документацию как систему» не означает «скопируй source tree».

Структура следует **аналитическим responsibility boundaries**, а не механически каталогам исходного кода.

## Канонические источники Aveli

- `methodology.ru.md` — принципы организации знания;
- `business/`, `backend/`, `frontend/`, `database/`, `integrations/` — локальные владельцы;
- `system/` — сквозной синтез.

Полный репозиторий:

https://github.com/branch-danya-dev/aveli-system-analysis

## Связь с SSAD

- [`../../04-knowledge-structure/storage-hierarchy/README.ru.md`](../../04-knowledge-structure/storage-hierarchy/README.ru.md)
- [`../../04-knowledge-structure/canonical-ownership/README.ru.md`](../../04-knowledge-structure/canonical-ownership/README.ru.md)
- [`../../03-analysis/synthesis/README.ru.md`](../../03-analysis/synthesis/README.ru.md)

Далее: [`access-ownership.ru.md`](access-ownership.ru.md)
