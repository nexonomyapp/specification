# Nexonomie — Dependency Model

## 1. Purpose

The dependency model is the core of Nexonomie.

A dependency represents a relationship through which a modification of one entity may influence another.

The system must distinguish a simple relationship from a dependency capable of transmitting an effect.

## 2. Directed relation

A dependency is represented conceptually as:

```text
A ─────────→ B
```

where A is the source and B is the target.

This means that a relevant change in A may affect B.

The exact semantics depend on the dependency type.

## 3. Dependency families

Initial families:

### Geographic

Examples:

- proximity;
- neighbourhood;
- accessibility;
- wind exposure;
- runoff;
- flood exposure;
- heat exposure.

### Economic

Examples:

- supplier;
- customer;
- employer;
- employee;
- economic flow.

### Social

Examples:

- attraction;
- repulsion;
- accessibility;
- usage;
- social influence.

### Environmental

Examples:

- habitat;
- pollination;
- thermal regulation;
- water regulation;
- air purification;
- biodiversity interaction.

### Infrastructure

Examples:

- service provision;
- transport dependence;
- utility dependence.

## 4. Dependency attributes

A dependency may have:

### Type

What kind of relationship is it?

### Direction

Which entity can influence which?

### Strength

How strong is the relationship?

The semantics of strength must be defined separately for each dependency type.

### Confidence

How confident are we that the dependency exists?

### Scope

Over what geographic or functional range does it operate?

### Temporal scope

When does it operate?

### Evidence

Why was the dependency created?

## 5. Evidence levels

Suggested status:

```text
OBSERVED
DOCUMENTED
INFERRED
AUTOMATICALLY_GENERATED
USER_VALIDATED
```

These should not be treated as equivalent.

## 6. Automatic dependencies

Some dependencies can be proposed automatically.

Examples:

- buildings within a given radius of a road;
- downstream entities along a runoff network;
- businesses connected to a known supplier;
- assets exposed to a heat source.

Automatic generation should produce candidate relationships that can be inspected.

## 7. Manual dependencies

Users may create dependencies when they possess local knowledge not available in the data.

Manual dependencies should store:

- creator;
- creation date;
- explanation;
- optional source;
- confidence.

## 8. Dependency propagation

If:

```text
A → B
B → C
C → D
```

then an intervention affecting A can potentially propagate to:

```text
B (distance 1)
C (distance 2)
D (distance 3)
```

This is a graph traversal problem.

The application must preserve the path.

## 9. Propagation is not automatically additive

The existence of multiple paths does not mean that effects should simply be added.

For example:

```text
A → B → D
A → C → D
```

does not imply that D receives two independent copies of the effect.

The future analysis engine must explicitly address convergence and double counting.

## 10. Dependency filters

An analysis should be able to restrict propagation by:

- dependency family;
- dependency type;
- confidence;
- strength;
- spatial scope;
- maximum depth.

## 11. Graph representation

Dependencies form a directed graph:

```text
G = (V, E)

V = assets
E = dependencies
```

The graph should support traversal, filtering and path extraction.

## 12. Important methodological distinction

The graph is a representation of possible influence relationships.

The graph alone does not constitute the nexonomic cost.

Quantification requires additional models describing:

```text
dependency
→ effect
→ magnitude
→ temporal behaviour
→ valuation
```
