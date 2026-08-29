# Example — Mobile Application

[Русская версия](README.ru.md)

> **Status:** synthetic example  
> **Purpose:** demonstrate local/server data ownership and synchronization boundaries.

## Scenario

A fictional personal-finance mobile application lets a user record expenses offline and optionally synchronize them between devices after sign-in.

Assumptions:

```text
Mobile client
Backend API
Local SQLite
Server PostgreSQL
External identity provider
```

## Possible SSAD Perspectives

```text
business/
database/
backend/
frontend/
integrations/
system/
```

This shape happens to resemble many mobile products, but it is not a methodology template.

## Ownership Example

```text
Expense working copy
→ local client while offline

Synced account-level expense state
→ backend after synchronization

Identity assertion
→ external identity provider

Product access decision
→ application backend
```

The example forces a distinction between:

```text
provider identity
≠
application authority

local working state
≠
server synchronized state
```

## Change Surface Example

Change request:

> Allow household members to share one expense ledger.

Likely Change Surface:

```text
Business              YES
System boundary       YES
Data ownership        YES
Backend               YES
Frontend              YES
Identity integration  YES
Trust / authorization YES
Failure model         YES
Acceptance            YES
```

The change is not merely a frontend feature because it changes ownership and authority.

## Intentionally Simplified

No real endpoint list, database schema, authentication protocol, or implementation repository is claimed.
