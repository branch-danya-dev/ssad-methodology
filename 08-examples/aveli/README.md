# Aveli · end-to-end SSAD application

Aveli is the first real-world SSAD application and validates the methodology on a product-shaped software system.

Full system-analysis repository:

https://github.com/branch-danya-dev/aveli-system-analysis

This section does not copy Aveli documentation. It shows how separate SSAD principles combine into one coherent system-analysis model.

## Why Aveli is a useful validation case

Aveli includes:

- a mobile client;
- a backend;
- a local professional workspace;
- server-controlled account and sessions;
- billing and RevenueCat;
- offline behavior;
- trust policy;
- external integrations;
- end-to-end user and system flows.

This makes it possible to validate not only folder structure, but boundaries, ownership, contracts, states, trust, failures and end-to-end consistency.

Aveli is intentionally complemented by the [`Enterprise Workplace Migration`](../enterprise-workplace-migration/README.md) application, which tests SSAD on a distributed enterprise transformation with a very different responsibility structure.

## Case structure

```text
Aveli
├─ repository-structure
│  └─ how knowledge structure follows system structure
├─ access-ownership
│  └─ who proves billing and who decides access
└─ offline-trust
   └─ how bounded trust enables operation without permanent connectivity
```

## How to read the case

Each slice answers four questions:

```text
1. What system question is being analyzed?
2. How does SSAD suggest reasoning about it?
3. What does that look like in Aveli?
4. Where is the canonical description?
```

Examples intentionally stay compact. Canonical truth remains in the Aveli repository.

> **An application explains the principle. Canonical project knowledge remains with its owner.**

Start: [`repository-structure.md`](repository-structure.md)
