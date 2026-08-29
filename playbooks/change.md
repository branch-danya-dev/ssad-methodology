# Playbook — Change

[Русская версия](change.ru.md)

## Use When

Use this playbook when a trustworthy `Baseline` or `Stable` system model already exists and a material change arrives.

Examples:

```text
new feature
changed business rule
new integration
provider replacement
technology replacement
schema change
security requirement
regulatory requirement
architecture change
data migration
```

## Primary Goal

Understand the **real Change Surface** before rewriting downstream design.

A material change should not begin with:

```text
Which file do I edit?
Which endpoint do I add?
Which technology do I install?
```

It begins with:

> **Which owners of system knowledge does this change affect?**

## Inputs

Minimum useful inputs:

```text
change request
reason / desired outcome
current baseline
known constraints
affected stakeholder intent
new external obligations, if any
```

The request may contain a proposed solution, but do not assume the proposal is the actual system need.

## Step 1 — Normalize the Change Request

Separate desired outcome from premature implementation.

Bad:

```text
Add Redis.
```

Better:

```text
Reduce repeated computation of access state under expected request load.
```

Bad:

```text
Call the DMS API after export.
```

Better:

```text
Allow successfully exported documents to be stored in the external DMS.
```

## Step 2 — Build the Change Surface

Perform a first-pass impact scan:

| Concern | Result |
|---|---|
| Business behavior | YES / NO / UNKNOWN |
| System boundary | YES / NO / UNKNOWN |
| Ownership | YES / NO / UNKNOWN |
| Data | YES / NO / UNKNOWN |
| Components | YES / NO / UNKNOWN |
| Internal interfaces | YES / NO / UNKNOWN |
| External integrations | YES / NO / UNKNOWN |
| Technology | YES / NO / UNKNOWN |
| Trust / security | YES / NO / UNKNOWN |
| Failure / recovery | YES / NO / UNKNOWN |
| Acceptance | YES / NO / UNKNOWN |
| Traceability | YES / NO / UNKNOWN |
| Operations | YES / NO / UNKNOWN |

`UNKNOWN` is useful. It means the change needs investigation before detail.

## Step 3 — Check Boundary Before Local Design

Ask:

```text
Does a new external actor or system appear?
Does data cross the system boundary differently?
Does responsibility move into or out of the system?
Does a previously internal interaction become external?
Does an external authority become part of a decision?
```

If YES, reopen system context and relevant perspectives.

## Step 4 — Check Ownership

Ask:

```text
Does canonical state move?
Does a new source of truth appear?
Does a former consumer become an owner?
Does a cache become authoritative?
Does an external provider now own part of the truth?
```

Do not design a contract until authority is understandable.

## Step 5 — Check Data and Lifecycle

For affected data determine:

```text
owner
creation
update authority
consumers
persistence
synchronization
migration
retention
deletion
privacy
reconciliation
```

A technology change may still create data-lifecycle impact.

## Step 6 — Check Interfaces and Integrations

For every changed crossing identify:

```text
producer
consumer
semantic contract
transport
authentication
authorization
compatibility
idempotency
retry
timeout
reconciliation
failure ownership
```

Keep internal interfaces separate from external integration boundaries.

## Step 7 — Check Components and Technologies

Now ask what implementation responsibilities move.

Technology is evaluated **after** responsibility impact.

A technology replacement should answer:

```text
What responsibility does it realize?
Where is it used?
Who depends on it?
What constraint motivated replacement?
Does ownership change?
Does runtime behavior change?
Does failure behavior change?
```

## Step 8 — Check Trust, Failure, and Recovery

For every new failure mode ask:

```text
What can fail?
Can partial success occur?
Who is authoritative during disagreement?
What state survives failure?
Can the operation be retried?
Is retry safe?
How is ambiguous outcome reconciled?
What must never be deleted or invalidated?
```

## Step 9 — Update Acceptance Before Declaring Design Complete

Define observable success and failure.

Examples:

```text
User can distinguish local success from remote failure.
Migration preserves all records that satisfy invariant X.
New provider failure does not revoke valid local state.
Old and new clients remain compatible during rollout.
```

A change without observable acceptance is not fully modeled.

## Step 10 — Update Canonical Owners in Dependency Order

Do not edit every affected document simultaneously.

Preferred order:

```text
business / decision change
→ boundary / ownership
→ data
→ interfaces / integrations
→ components
→ technologies
→ system synthesis
→ acceptance / traceability
```

Only update documents actually affected.

## Step 11 — VERIFY the Delta

Verify both:

```text
new knowledge ↔ new knowledge
```

and:

```text
new knowledge ↔ unchanged baseline
```

A change can be internally coherent and still break an old invariant.

Check:

```text
old invariants
compatibility
data preservation
authority
failure behavior
cross-references
diagrams
acceptance
```

## Step 12 — Restabilize

Affected knowledge may temporarily move:

```text
Stable
→ Draft / Baseline
→ Stable
```

Unaffected knowledge remains Stable.

Do not destabilize the entire repository because one feature changed.

## Expected Outputs

A material change should leave:

- normalized change statement;
- Change Surface;
- affected-owner list;
- changed boundary/ownership model where relevant;
- changed data/interface/component knowledge;
- new or changed invariants;
- updated acceptance;
- updated traceability;
- verification result;
- revised maturity status.

## Branch: Integration Change

Increase emphasis on:

```text
external authority
authentication
provider contract
idempotency
retry
timeout
reconciliation
provider-specific failure behavior
```

Worked example: [`../examples/desktop-plugin/changes/dms-upload/`](../examples/desktop-plugin/changes/dms-upload/)

## Branch: Architecture Change

If responsibility moves between major components:

```text
reopen BOUND
→ reopen OWN
→ rebuild affected downstream knowledge
```

Do not treat architecture change as a collection of local edits.

## Branch: Technology Replacement

If responsibility does not change:

```text
ownership may remain stable
```

but still verify:

```text
runtime behavior
failure modes
operations
migration
compatibility
performance / capacity constraints
```

## Branch: Data Migration

Add explicit checks for:

```text
source authority
target authority
cutover
dual-write / read strategy
rollback
identity mapping
loss prevention
compatibility
post-migration verification
```

## Common Failure Modes

### Starting from the proposed solution
The request may contain a design assumption rather than the actual need.

### Editing only the most obvious component
A feature may cross business, data, trust, integration, and acceptance boundaries.

### Treating "NO IMPACT" as a guess
If you have not checked the perspective, use `UNKNOWN`.

### Forgetting old invariants
New behavior must coexist with still-valid baseline guarantees.

### Creating a new perspective too early
A new folder should appear only when the changed system creates a new canonical owner.

## Exit Criteria

The change is ready to return to Stable when:

```text
Change Surface is resolved
affected ownership is explicit
new contracts match authority
data lifecycle is coherent
new failure modes have recovery semantics
old valid invariants still hold or are deliberately changed
acceptance is observable
traceability explains why each major change exists
```
