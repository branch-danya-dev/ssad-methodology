# Playbook — Existing System

[Русская версия](existing-system.ru.md)

## Use When

Use this playbook when the system already exists, but the analytical baseline is missing, stale, fragmented, contradictory, or shaped too closely by implementation details.

Typical situations:

```text
legacy system
undocumented service
documentation migration
architecture reconstruction
handover
audit
pre-refactoring analysis
pre-migration analysis
```

## Primary Goal

Reconstruct a **trustworthy current-state model** before target-state design begins.

The first job is not to improve the architecture.

The first job is to understand the architecture that actually exists.

## Inputs

Prefer direct evidence:

```text
source code
runtime configuration
API contracts
database schemas
deployment manifests
provider contracts
tests
logs
observed runtime behavior
existing documentation
stakeholder knowledge
incident history
```

Existing documentation is evidence, not automatic truth.

## Step 1 — DISCOVER: Build an Evidence Map

Inventory evidence by trust and relevance.

For each important statement classify:

```text
VERIFIED
INFERRED
OPEN
```

Record contradictions explicitly.

Example:

```text
Old document:
"Service A owns customer status"

Database:
customer_status stored in Service B

Runtime:
Service A reads status from Service B

→ ownership claim is OPEN / likely stale
```

## Step 2 — Separate Current State from Target State

Create a hard conceptual boundary:

```text
CURRENT
≠
TARGET
```

Do not silently rewrite existing behavior into the architecture you want.

If a better design is proposed, mark it as proposal or target state.

## Step 3 — BOUND the Real System

Reconstruct:

```text
actual actors
actual external systems
actual runtime components
actual data crossings
actual authority boundaries
actual operational dependencies
```

A deployed dependency is part of current-state analysis even if nobody documented it.

## Step 4 — OWN: Reconstruct Canonical Responsibility

For every important state or decision ask:

```text
Who actually writes it?
Who can change it?
Who is queried when components disagree?
Where does authoritative persistence live?
Who only caches or mirrors it?
```

Implementation evidence may reveal ownership that old diagrams hide.

## Step 5 — Derive Perspectives from the Existing System

Do not preserve legacy folders merely because they exist.

Also do not delete them yet.

First identify the new canonical owners.

Possible result:

```text
business/
services/
data/
messaging/
integrations/
operations/
system/
```

## Step 6 — Migrate Legacy Knowledge Safely

Before removing or restructuring old documentation:

```text
1. establish new canonical owner
2. inspect old files for unique/orphan knowledge
3. migrate unique knowledge
4. repair cross-references
5. remove duplicate or stale content
6. run consistency review
```

Never delete a legacy file before checking whether it contains unique knowledge.

## Step 7 — MODEL Current Behavior

Prioritize:

```text
actual business/system behavior
actual data ownership
actual interfaces
actual failure behavior
actual security/trust boundaries
actual technology usage
```

When implementation contradicts intended behavior, document both:

```text
CURRENT
→ what exists

INTENDED / TARGET
→ what should change
```

## Step 8 — CONNECT Evidence to Knowledge

Trace material claims back to evidence where practical.

Examples:

```text
API ownership
→ OpenAPI + producer code

database ownership
→ schema + write path

provider behavior
→ provider contract

runtime dependency
→ deployment/configuration
```

This reduces the risk of turning inference into fact.

## Step 9 — SYNTHESIZE the Current System

Only after owner-local knowledge is coherent, build:

```text
current system context
component model
end-to-end flows
trust / authority map
cross-component data movement
system invariants
current failure model
```

The system view summarizes; it does not replace canonical owners.

## Step 10 — VERIFY

Cross-check especially:

```text
documentation ↔ implementation
diagram ↔ runtime topology
API producer ↔ consumer
schema ↔ data model
stated owner ↔ actual write path
current state ↔ target proposal
```

Contradictions must be resolved or left explicitly `OPEN`.

## Step 11 — STABILIZE

Promote only sufficiently supported current-state knowledge.

Typical result:

```text
Stable
→ high-confidence boundaries and ownership

Baseline
→ sufficiently supported behavior/model

Draft
→ implementation-specific areas still under investigation
```

## Expected Outputs

- evidence inventory;
- current-state boundary;
- canonical ownership map;
- explicit current vs target distinction;
- migrated system-shaped documentation;
- traceability to implementation evidence;
- system synthesis;
- open-question register;
- maturity classification.

## Branch: Legacy Documentation Migration

If the main task is "move old docs into SSAD", do **not** begin by moving files.

Begin with ownership reconstruction.

Migration is a consequence of understanding, not a file-management exercise.

## Branch: Pre-Refactoring

If a refactoring is planned:

```text
Existing System playbook
→ Stable current baseline
→ Change playbook
→ target refactoring
```

Do not collapse current-state reconstruction and target architecture into one pass.

## Common Failure Modes

### Trusting documentation over runtime evidence
Old documentation may describe intent, not reality.

### Trusting code without context
Code can contain dead paths, compatibility logic, or temporary workarounds.

### Treating every database table as a domain owner
Persistence location alone does not always define semantic ownership.

### "Cleaning up" contradictions
Contradiction is information. Preserve it until resolved.

### Migrating folders before knowledge
This reproduces old ambiguity in a new tree.

## Exit Criteria

The system is ready to become a baseline when:

```text
current boundary is explicit
major owners are evidence-supported
current and target states are separated
legacy unique knowledge is preserved
system views agree with component evidence
material contradictions are resolved or OPEN
```

After that, use [`change.md`](change.md) for target-state evolution.
