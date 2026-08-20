# Nexonomie — Scenario Model

## 1. Purpose

A Scenario describes what a project does to the territory.

It must remain separate from the collective representation of the territory.

## 2. Initial state

The initial state is derived from assets present in the relevant study area.

The system should not physically delete these assets when the project proposes to remove them.

Instead, the scenario records an intervention.

Example:

```text
Asset: TREE-123
Scenario action: REMOVE
```

The collective asset remains available.

## 3. Intervention types

Initial actions:

```text
REMOVE
ADD
MODIFY
MOVE
AFFECT
```

### REMOVE

The asset is expected to disappear.

### ADD

A new asset is expected to appear.

### MODIFY

The asset remains but one or more properties change.

### MOVE

The asset changes geographic position.

### AFFECT

The asset remains but its state or functioning is affected.

## 4. Before/after representation

For modifications, the scenario should conceptually support:

```text
before
   ↓
intervention
   ↓
after
```

Properties may therefore be represented as:

```text
properties_before
properties_after
```

## 5. Scenario-local assets

Some future assets do not yet exist in the collective territorial database.

For example:

- planned building;
- planned park;
- planned road;
- planned pond.

These may initially exist only within the scenario.

They may later be promoted to collective assets when the project is realized.

## 6. Multiple scenarios

A project should eventually support:

```text
Project
├── Existing situation
├── Scenario A
├── Scenario B
└── Scenario C
```

The same collective assets can participate in several scenarios.

## 7. Scenario comparison

The architecture should eventually support comparison between scenarios.

For example:

```text
Scenario A → estimated effects
Scenario B → estimated effects
Scenario C → estimated effects
```

This is important for decision support.

## 8. Directly affected assets

The directly affected set is determined from scenario interventions.

Example:

```text
REMOVE TREE-1
REMOVE BUILDING-7
MODIFY ROAD-3
ADD PARK-2
```

These assets constitute the initial seeds for propagation.

## 9. Indirectly affected assets

Indirectly affected assets are discovered through dependencies.

They should not be copied into the scenario.

Instead, the analysis records their participation.

## 10. Scenario isolation

A scenario must never silently alter:

- collective asset properties;
- collective geometry;
- collective dependencies;
- scientific references.

Any project-specific modification must remain project-specific.

## 11. Scenario status

Suggested states:

```text
DRAFT
IN_REVIEW
VALIDATED
ARCHIVED
```

Only validated scenarios should eventually be used for official analyses.

## 12. Auditability

Changes to a scenario should eventually be traceable.

At minimum, preserve:

- author;
- timestamp;
- changed field;
- previous value;
- new value.
