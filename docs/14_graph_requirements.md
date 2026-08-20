# Nexonomie — Dependency Graph Requirements

## 1. Purpose

The dependency graph provides an abstract representation of the territorial network.

It complements the geographic map rather than replacing it.

## 2. Graph model

```text
Nodes = Assets
Edges = Dependencies
```

Edges are directed when the dependency is directional.

## 3. Initial view

The initial graph should not necessarily display every asset.

It should start from the directly affected assets and progressively reveal the network.

## 4. Progressive exploration

A useful interaction is:

```text
Directly affected nodes
        ↓
click node
        ↓
show direct dependencies
        ↓
click neighbour
        ↓
expand further
```

This avoids overwhelming the user.

## 5. Visual encoding

Different dimensions may be encoded through:

- node shape;
- node size;
- line style;
- edge thickness;
- labels;
- restrained colour coding.

Do not rely on colour alone.

## 6. Dependency types

The graph should allow filtering by dependency family.

Example:

```text
[✓] Geographic
[✓] Economic
[ ] Social
[✓] Environmental
[ ] Infrastructure
```

## 7. Node states

Possible states:

```text
DIRECTLY_AFFECTED
INDIRECTLY_AFFECTED
SELECTED
EXPANDED
COLLAPSED
UNVALIDATED
```

## 8. Path inspection

Selecting a target node should allow the user to inspect how it became connected to the intervention.

Example:

```text
Project
 ↓
Tree A
 ↓ cooling
Building B
 ↓ occupancy
Business C
```

The exact semantics depend on the dependency types and later effect models.

## 9. Graph depth

The user should be able to choose a maximum propagation depth.

Example:

```text
Depth 1
Depth 2
Depth 3
Depth 5
```

The application should clearly indicate the chosen depth.

## 10. Graph/map interaction

The graph and map must eventually be synchronized.

Selecting a node in the graph should:

- highlight the corresponding asset;
- center the map;
- open or focus its inspector.

Selecting an asset on the map should:

- highlight its node;
- reveal it in the graph if necessary.

## 11. Explainability

The graph should support the question:

> Why is this entity part of the analysis?

The answer should identify the dependency path and relevant evidence.

## 12. Large graphs

The application should avoid attempting to render thousands of nodes simultaneously when unnecessary.

Use:

- progressive expansion;
- filtering;
- clustering;
- level-of-detail;
- server-side graph queries where appropriate.
