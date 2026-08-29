# Change Analysis Workflow

[Русская версия](change-analysis.ru.md)

## Purpose

Use this workflow when a stable or partially stable system receives a new feature, changed business rule, integration, data-model change, technology replacement, architecture change, security/regulatory constraint, or provider/platform change.

## 1. Define the Change Request

State the requested outcome without prematurely turning it into an implementation solution.

Bad:

```text
Add Redis.
```

Better:

```text
Reduce repeated computation of access state under expected request load.
```

## 2. Build the Change Surface

```text
Change:
Reason:

Business impact:
Boundary impact:
Data impact:
Component impact:
Interface impact:
Integration impact:
Technology impact:
Trust/security impact:
Failure/recovery impact:
Acceptance impact:
Traceability impact:
```

Use `YES / NO / UNKNOWN` for the first pass.

## 3. Check Boundary Impact

Ask whether the system boundary changes, a new external actor appears, data crosses the boundary differently, or responsibility moves between components.

## 4. Check Ownership Impact

Ask whether decision authority changes, canonical state moves, a new source of truth appears, or a consumer becomes an owner.

## 5. Check Data Impact

Check entities, ownership, lifecycle, migration, synchronization, retention, privacy, and physical boundaries.

## 6. Check Interface and Integration Impact

Identify changed internal/external contracts, compatibility, retry/idempotency, reconciliation, trust, and authentication.

## 7. Check Component and Technology Impact

Do not treat technology replacement as the change itself unless technology is the actual constraint. Identify changed responsibilities first.

## 8. Check Trust, Failure, and Recovery

Ask:

```text
What new failure modes exist?
Who is authoritative during disagreement?
What happens offline?
Can partial success occur?
How is recovery performed?
```

## 9. Update Acceptance and Traceability

Every high-impact change should explain the observable success condition and why each major technical change exists.

## 10. Verify and Stabilize

Run the relevant quality gates and return affected knowledge to `Stable` when evidence supports it.

## Example — Cloud Workspace Sync

```text
Business              YES
System boundary       YES
Data ownership        YES
Backend               YES
Frontend              YES
External integration  MAYBE
Trust / authority     YES
Failure model         YES
Acceptance            YES
Traceability          YES
```

This is a system-boundary change, not merely "a backend task".
