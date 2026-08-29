# Evidence and Readiness · enterprise migration

[English version](evidence-readiness.md)

## Системный вопрос

Кто владеет migration readiness, если evidence для решения распределён между несколькими независимыми командами и системами?

## Исходная сложность

Рабочее место может зависеть от:

- standard и specialized software;
- corporate services;
- access rights и certificates;
- ограничений Information Security;
- network/security rules;
- возможностей migration automation;
- hardware/peripherals;
- business-role-specific workflows;
- vendor remediation.

Разные команды знают разные части этой реальности.

Например:

```text
Software Support
→ software/functionality evidence

Information Security
→ security/access evidence

Infrastructure Automation
→ tooling/infrastructure evidence

Workplace Support
→ workplace and operational evidence

Vendor / Development
→ remediation evidence
```

Из этого нельзя делать вывод, что каждый evidence provider владеет итоговым migration-readiness decision.

## Рассуждение по SSAD

Нужно разделить **evidence authority** и **system decision authority**.

```text
SPECIALIZED DOMAIN
владеет evidence о своей области
        ↓
MIGRATION READINESS
потребляет evidence
        ↓
GREEN / YELLOW / RED
```

Migration model не становится authoritative над внутренностями Information Security, software support или infrastructure.

Но и эти домены по отдельности не определяют aggregate migration state.

> **Evidence распределён. Системный смысл всё равно требует явного владельца.**

## Readiness как time-sensitive decision

Readiness — не immutable field.

```text
Evidence set at time T1
→ GREEN

new blocker / compatibility regression / access change at T2
→ previous decision reopened
→ new evaluation
→ YELLOW or RED
```

Поэтому technical projection позднее представляет readiness как evaluation snapshots, а не как `readinessStatus` внутри migration schedule.

## Blockers и evidence

Exception способен изменить readiness, не становясь владельцем underlying external problem.

```text
Software domain
→ owns underlying incompatibility

Exceptions
→ owns migration blocker and recovery impact

Readiness
→ decides whether current evidence permits migration
```

Такое трёхстороннее разделение не позволяет одному support ticket или compatibility flag превратиться в полную migration model.

## Урок для Collaboration

Cross-team review становится точнее, когда участники подтверждают claims внутри своей authority.

Вместо общего вопроса:

> «Это рабочее место готово?»

лучше задавать узкие вопросы:

```text
Доступна ли требуемая функциональность?
Валиден ли требуемый доступ?
Поддерживает ли migration tooling этот профиль?
Активен ли известный blocker?
Проверено ли remediation?
```

После этого readiness owner синтезирует подтверждённые claims в migration decision.

## Каноническая проектная истина

Полная модель:

https://github.com/branch-danya-dev/enterprise-workplace-os-migration

Основные области:

- `readiness/evidence-model.md`
- `readiness/decision-model.md`
- `exceptions/blockers-and-recovery.md`
- `integrations/boundary-contracts.md`
- `system/invariants.md`

## Какие главы SSAD демонстрирует кейс

- [`03-analysis/ownership/`](../../03-analysis/ownership/)
- [`03-analysis/integrations/`](../../03-analysis/integrations/)
- [`03-analysis/trust/`](../../03-analysis/trust/)
- [`05-collaboration/knowledge-contribution/`](../../05-collaboration/knowledge-contribution/)
- [`05-collaboration/validation/`](../../05-collaboration/validation/)
- [`05-collaboration/decision-resolution/`](../../05-collaboration/decision-resolution/)

Далее: [`technical-projection.ru.md`](technical-projection.ru.md)
