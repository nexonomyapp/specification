# Nexonomie — Scientific Reference Model

## 1. Purpose

The reference layer contains scientific and institutional knowledge used by Nexonomie.

It is separate from territorial data and project data.

## 2. Reference

A Reference is a source document or dataset.

Examples:

- peer-reviewed publication;
- governmental report;
- institutional database;
- national reference framework;
- technical documentation.

A Reference should contain sufficient bibliographic information to identify the source.

## 3. Parameter

A ParameterDefinition defines a reusable scientific quantity.

Example:

```text
TREE_COOLING_POWER_PER_CANOPY_AREA
unit: W/m²
```

A parameter should have:

- definition;
- unit;
- source;
- valid range;
- uncertainty if known;
- geographical scope;
- temporal scope.

## 4. Model

A ScientificModel defines a transformation between quantities.

Conceptually:

```text
inputs → model → output
```

Example:

```text
tree species
tree height
canopy area
       ↓
cooling model
       ↓
cooling capacity
```

## 5. Model provenance

Every scientific model must identify its sources.

A model may cite multiple references.

## 6. Versioning

Models and parameters must be versioned.

An analysis should store the versions used.

This ensures that an old analysis remains interpretable even after the reference model evolves.

## 7. Local adaptation

The platform must allow local adjustments when justified.

For example:

```text
national reference
       ↓
local parameterisation
       ↓
project estimate
```

Local adjustments must explicitly identify:

- what was changed;
- why;
- by whom;
- on what evidence.

## 8. Ecosystem service catalogue

The catalogue should define services independently from particular assets.

Example:

```text
Service:
Thermal regulation

Potential providers:
TREE
FOREST
PARK
WETLAND
```

The service model then determines how the properties of each provider influence the service.

## 9. Conversion chain

A service may be converted through several steps.

Example:

```text
Asset properties
      ↓
Service intensity
      ↓
Physical equivalent
      ↓
Human/infrastructure equivalent
      ↓
Economic cost
      ↓
Annual value
```

Every step should be represented explicitly.

## 10. Scientific status

Suggested status values:

```text
DRAFT
REVIEWED
VALIDATED
DEPRECATED
```

Only validated models should normally be used for official analyses.

## 11. No unsupported values

If a model requires a coefficient for which no validated source exists, the system must not invent one.

It should instead flag the missing parameter.

## 12. Traceability

A user inspecting a result should eventually be able to navigate:

```text
Result
 ↓
Valuation model
 ↓
Scientific model
 ↓
Parameter
 ↓
Reference
```
