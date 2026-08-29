# Roadmap SSAD

[English version](ROADMAP.md)

Этот roadmap описывает **зрелость методологии**, а не feature backlog.

Цель — не продолжать бесконечно добавлять главы. Цель — доказать, что SSAD целостна, обучаема, практична и достаточно стабильна для применения к разным системам.

## Текущий этап

У SSAD уже есть полный reader-first каркас:

```text
Foundation
→ Workflow
→ Analysis
→ Knowledge Structure
→ Collaboration
→ Change
→ Practice
→ Examples
```

Теперь задокументированы два существенно разных real-world applications:

```text
Aveli
→ product-shaped software system

Enterprise Workplace Migration
→ distributed enterprise transformation / existing-system migration
```

Текущая фаза — **comparative validation и stabilization**: проверить, какие принципы остаются стабильными на обеих системах, собирать friction points и менять ядро только когда этого требует evidence.

## Что должно означать v1.0

SSAD v1.0 должна означать:

> **Ядро методологии достаточно стабильно, чтобы дальнейшие изменения в основном улучшали формулировки, evidence, примеры и практические маршруты, а не регулярно перестраивали концептуальный фундамент.**

### Критерии v1.0

#### 1. Концептуальная стабильность

- [ ] Foundation больше не требует структурных переписываний.
- [ ] Workflow и analytical mechanics не конкурируют как два альтернативных lifecycle.
- [ ] Boundaries, responsibility, ownership, evidence, authority и canonical knowledge используются последовательно.
- [ ] Local analysis и system synthesis имеют чётко разделённые ответственности.
- [ ] Change analysis переиспользует основную модель SSAD, а не создаёт параллельную методологию.

#### 2. Проверка на реальных системах

- [ ] Aveli продолжает подтверждать методологию после существенных изменений системы.
- [x] Добавлен хотя бы один дополнительный real-world кейс с существенно другой структурой.
- [x] Хотя бы один integration-heavy или event-driven кейс проверяет cross-boundary reasoning.
- [x] Хотя бы один existing-system / migration кейс проверяет Change Surface, compatibility и selective reopening.

Validation evidence теперь включает:

- [`08-examples/aveli/`](08-examples/aveli/) — product boundaries, access ownership и bounded offline trust;
- [`08-examples/enterprise-workplace-migration/`](08-examples/enterprise-workplace-migration/) — distributed responsibility, readiness evidence, state decomposition, migration/change reasoning и ownership-aware technical projection.

Второй application важен потому, что SSAD создала для него system-shaped repository, совсем не похожий на Aveli, но сохранила те же reasoning principles.

#### 3. Качество обучения

- [ ] Новый аналитик может пройти Foundation → Workflow → Analysis без внешнего объяснения.
- [ ] Каждая core-глава имеет понятную проблему, метод, пример и условие проверки результата.
- [ ] Practice checklist'ы стабильно ведут обратно в глубокие канонические главы.
- [ ] RU и EN семантически эквивалентны по core content.
- [ ] Важные термины понятны из контекста без необходимости в огромном glossary.

#### 4. Качество навигации

- [ ] Root README остаётся компактным landing page.
- [ ] Нет активной legacy-документации, конкурирующей с reader-first структурой.
- [ ] Cross-links отражают реальные связи знаний, а не декоративную навигацию.
- [ ] На локальный вопрос можно ответить без чтения несвязанных разделов.
- [ ] Большой репозиторий по-прежнему ощущается локально маленьким.

#### 5. Contribution model

- [x] Принципы contribution описаны.
- [ ] Для methodology-level предложений есть повторяемый evidence/review process.
- [ ] Example contributions явно отделяют учебный контекст от canonical project truth.
- [ ] Правила Issues / Discussions будут определены, когда начнутся реальные внешние contributions.

#### 6. Готовность к публикации

- [ ] Осознанно выбрана и добавлена license.
- [ ] GitHub description и topics ясно объясняют system analysis, knowledge architecture и границы методологии.
- [ ] Стабильный v1.0 отмечен release/tag с короткими release notes.
- [ ] Changelog отделяет исследовательские исторические фазы от стабильной reader-first методологии.

## Ближайшие приоритеты

### P0 — сравнивать, проверять, не расширять

1. продолжать применять SSAD к существенным изменениям Aveli и другим реальным системам;
2. сравнивать friction points product-shaped и transformation-shaped applications;
3. искать неоднозначности, дубли и отсутствующие reasoning steps, повторяющиеся между кейсами;
4. исправлять только проблемы, подтверждённые evidence.

### P1 — расширять validation только ради нового риска

Milestone второго real-world application выполнен.

Третий кейс имеет смысл только если проверяет существенно новую проблему, а не добавляет ещё одну витрину.

Возможные будущие формы validation:

- strongly event-driven backend platform;
- desktop или host-application plugin ecosystem;
- integration-heavy internal service с versioned contracts;
- система со значимой data migration или distributed consistency.

Вопрос теперь не «есть ли у нас ещё один кейс?», а:

> **Какое ещё непроверенное свойство системы способно сломать текущую модель SSAD?**

### P2 — contribution и release hygiene

- выбрать лицензию;
- определить conventions для Issues / Discussions, если начнётся внешнее участие;
- определить release/versioning semantics;
- подготовить v1.0 release notes после выполнения критериев выше.

## Чего намеренно нет в roadmap

SSAD сейчас **не планирует** отдельную top-level главу под каждый аналитический артефакт, notation или технологию.

Нет roadmap вида:

```text
09-UML
10-BPMN
11-SQL
12-Kafka
13-OpenAPI
```

Эти инструменты могут появляться внутри соответствующих системных вопросов и примеров.

Новая область методологии должна появиться только тогда, когда у неё есть отдельная аналитическая ответственность, которую нельзя чисто разместить в существующей модели.

## Как принимать новые roadmap items

Предложение должно отвечать:

```text
Какая реальная проблема появилась?
Какая существующая область SSAD не справилась?
Какое evidence подтверждает проблему?
Нужен ли действительно новый концепт?
Можно ли улучшить существующего владельца?
Как проверить изменение?
```

## Долгосрочное направление

Желаемая зрелая форма SSAD — маленькое концептуальное ядро и богатый слой evidence:

```text
стабильные принципы
+
стабильная reasoning model
+
сильная навигация
+
много real-world validations
+
практические task routes
```

А не:

```text
бесконечно растущая taxonomy
+
бесконечно растущая обязательная структура
```

Это различие является одним из центральных принципов проекта.
