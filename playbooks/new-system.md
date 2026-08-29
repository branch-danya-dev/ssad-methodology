# Playbook — New System

[Русская версия](new-system.ru.md)

## Use When

Use this playbook for a new product, service, plugin, platform, or major subsystem when there is no trustworthy existing system baseline to reconstruct.

## Primary Goal

Create the **minimum trustworthy analytical baseline** that downstream design can safely depend on.

The goal is not to produce every possible document.

## Inputs

Useful inputs may include:

```text
business problem
stakeholder goals
product idea
known users / actors
constraints
external platforms
regulatory requirements
existing organizational standards
initial technical assumptions
```

Unknowns are acceptable. Hidden unknowns are not.

## Step 1 — DISCOVER: Build the Evidence Inventory

Collect what is actually known.

Classify important statements as:

```text
VERIFIED
INFERRED
OPEN
```

Do not turn a preferred architecture into verified truth.

### Output

- initial evidence inventory;
- vocabulary;
- open-question register;
- known constraints.

## Step 2 — BOUND: Define the System of Interest

State:

```text
what problem the system solves
who interacts with it
what is in scope
what is out of scope
what external systems exist
what authority stays outside the system
```

Do not start with folders.

### Gate

A reader should be able to explain where the system starts and ends.

If not, stay here.

## Step 3 — OWN: Establish Responsibility and State Ownership

For every material responsibility or state ask:

```text
Who decides?
Who stores canonical state?
Who may change it?
Who consumes it?
Who verifies it?
```

Look specifically for competing sources of truth.

### Gate

Important state must not have two accidental canonical owners.

## Step 4 — Derive Analytical Perspectives

Only now choose the physical knowledge owners.

Examples:

```text
business/
plugin/
host-application/
filesystem/
system/
```

or:

```text
business/
services/
messaging/
data/
operations/
system/
```

Create a perspective because the system needs it, not because another SSAD repository has it.

## Step 5 — MODEL in Dependency Order

Model only the detail justified by stabilized upstream knowledge.

Typical order:

```text
business rules / requirements
→ data ownership / lifecycle
→ responsibilities
→ interfaces / integrations
→ state / failure behavior
→ technologies and usage
```

This is not a mandatory artifact list.

Skip what does not exist.

## Step 6 — CONNECT

Add the graph across the hierarchy.

Connect:

```text
business rule ↔ requirement
requirement ↔ component
owner ↔ consumer
producer ↔ interface ↔ consumer
technology ↔ usage
data owner ↔ persistence / consumer
requirement ↔ acceptance
```

Do not duplicate canonical definitions just to improve navigation.

## Step 7 — SYNTHESIZE

Create whole-system knowledge only after local owners are sufficiently understood.

Typical system-level synthesis:

```text
system context
component relationships
end-to-end flows
trust / authority map
cross-component data movement
system invariants
whole-system failure scenarios
```

## Step 8 — VERIFY

Cross-check at least:

```text
business ↔ technical behavior
ownership ↔ contracts
logical data ↔ persistence
producer ↔ consumer
diagram ↔ prose
requirement ↔ acceptance
system synthesis ↔ local owners
```

A contradiction reopens upstream knowledge.

Do not "fix" it only in the system summary.

## Step 9 — STABILIZE

Promote knowledge deliberately:

```text
Draft
→ Baseline
→ Stable
```

Stable means safe enough to act as upstream input.

It does not mean implementation is complete.

## Expected Outputs

A successful pass normally leaves:

- explicit scope and boundary;
- explicit ownership;
- system-shaped perspectives;
- enough behavior/data/interface knowledge for the next engineering decisions;
- traceability;
- open questions;
- system synthesis;
- maturity classification.

## Stop / Reopen Conditions

Reopen earlier work when:

- a new actor changes scope;
- responsibility has no clear owner;
- two components claim the same canonical state;
- a contract requires behavior not supported by business rules;
- an implementation constraint invalidates an assumption;
- verification exposes contradiction.

## Common Failure Modes

### Starting from a folder template
Result: artificial owners and empty directories.

### Designing API before ownership
Result: contracts encode accidental responsibility.

### Choosing technologies before boundaries
Result: architecture is justified by tools rather than system needs.

### Treating every unknown as a blocker
Result: analysis never progresses.

### Treating no unknown as important
Result: assumptions silently become architecture.

## Exit Criteria

Use the baseline as a foundation for implementation or later change when:

```text
scope is understandable
major owners are explicit
important behavior is traceable
system synthesis agrees with local knowledge
material contradictions are resolved
remaining uncertainty is explicit
```

Worked example: [`../examples/desktop-plugin/walkthrough/`](../examples/desktop-plugin/walkthrough/)
