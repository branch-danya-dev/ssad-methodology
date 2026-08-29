# Change Surface

Initial Scope shows where a change starts.

Change Surface shows:

> **Which parts of the system and its knowledge can actually be affected?**

It is a map of affected responsibility areas and knowledge types, not a dump of all dependencies.

```text
INITIAL SCOPE
    ↓
AFFECTED RESPONSIBILITIES
    ↓
AFFECTED OWNERS
    ↓
LOCAL MODELS
    ↓
INTERFACES / INTEGRATIONS
    ↓
FLOWS / TRUST / FAILURES
    ↓
CHANGE SURFACE
```

For each potentially affected area, inspect behavior, states, data, interfaces, integrations, flows, trust, failures and invariants.

Useful impact labels are:

```text
DIRECT
INDIRECT
POTENTIAL
OUT OF SCOPE
```

A good Change Surface explains what changes directly, what depends on it, who owns those areas, which contracts and flows cross them, which invariants may be broken, and which checked areas remain unaffected.

Dependency does not automatically mean impact.

Next: [`../compatibility-risk/`](../compatibility-risk/).
