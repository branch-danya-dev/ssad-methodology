# 05 · Collaboration

Этот раздел отвечает на вопрос:

> **Как системно-аналитическое знание взаимодействует с реальной командой разработки?**

SSAD не рассматривает документацию как личный архив аналитика и не предполагает одноразовую передачу готового документа в разработку.

## Двусторонняя модель

```text
Client / Product / Business
            ↕
            SA
            ↕
     SSAD knowledge base
      ↙      ↓       ↘
Architect   Dev       QA
      ↖      ↑       ↗
       Implementation
            ↓
         Evidence
            ↓
     knowledge update
```

Команда одновременно:

- поставляет входные данные;
- проверяет аналитические решения;
- использует системное знание;
- обнаруживает ограничения;
- возвращает новые факты;
- участвует в стабилизации знания.

## Участники

SSAD рассматривает взаимодействие как минимум с:

```text
Client / Requester
Product Owner / Business
Business Analyst
System Analyst
Architect
Developer
QA
DevOps / Operations
Security
Integration Owner
Support
```

Для каждого участника важно понимать не только «когда с ним поговорить», но и **какое знание он может подтвердить или опровергнуть**.

## Основные темы раздела

```text
stakeholders
requirements communication
review
team validation
grooming
development support
QA / acceptance
integration teams
decision feedback
knowledge feedback loop
```

## Принцип

> **Системное знание не передаётся команде как законченный артефакт. Оно проверяется и развивается вместе с командой.**

Следующий раздел: [`06-change/`](../06-change/).
