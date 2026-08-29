# Roles and Knowledge Stewardship

[Русская версия](roles-and-stewardship.ru.md)

SSAD separates **decision ownership** from **documentation stewardship**.

| Knowledge | Typical decision owner | Typical documentation steward |
|---|---|---|
| Business goal / policy | Product owner / stakeholder / domain owner | BA / SA |
| Business rule | Domain / product owner | BA / SA |
| System boundary | Product + architecture stakeholders | SA / architect |
| API contract | Owning system/team | SA / developers |
| Data ownership | Owning system/team | SA / architect / data owner |
| Implementation | Engineering team | Developers |
| Verification | Product/system team | QA / SA / developers |
| Operational policy | Operations/platform owner | Ops / SRE / architect |

## Role Contributions

- **Business Analyst** protects business intent, process meaning, stakeholder goals, and business rules.
- **System Analyst** protects consistency, boundaries, contracts, data ownership, traceability, and business-to-technical continuity.
- **Developer** provides implementation evidence and validates feasibility and actual behavior.
- **QA** validates observable behavior and repeatable acceptance.
- **Architect** validates cross-system boundaries and high-impact architecture decisions.
- **Product Owner / Stakeholder** owns product decisions and validates business intent.

## No-BA Context

If no BA exists, the SA may steward business documentation, but should preserve:

```text
business decision
≠
technical design decision
```

Missing business decisions should be validated with the appropriate product/domain owner instead of inferred from technical convenience.
