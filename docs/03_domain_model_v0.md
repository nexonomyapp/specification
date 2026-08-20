# Nexonomie — Domain Model v0

This document defines the first conceptual data model. It is deliberately implementation-independent.

## 1. User

Represents an authenticated person using the application.

Main attributes:

- id
- email
- name
- created_at

A user may own or participate in several projects.

## 2. Project

Represents an urban or territorial development study.

Main attributes:

- id
- name
- description
- owner_id
- created_at
- updated_at
- status

A project has one principal study area and one or more scenarios.

## 3. StudyArea

Represents the geographical territory analysed by a project.

Main attributes:

- id
- project_id
- geometry
- coordinate_reference_system
- description

The study area may contain or surround the intervention area.

## 4. Asset

An Asset is a geographically identifiable entity relevant to territorial analysis.

Examples:

- tree;
- forest;
- pond;
- hedge;
- park;
- building;
- dwelling;
- business;
- road;
- agricultural area;
- public facility.

Main attributes:

- id
- asset_type_id
- geometry
- name
- description
- properties
- source
- created_at
- updated_at

An Asset may exist independently of a project and may be reused by several projects.

## 5. AssetType

Defines the semantic category of an asset.

Examples:

- TREE
- FOREST
- POND
- HEDGE
- PARK
- BUILDING
- BUSINESS
- ROAD
- AGRICULTURAL_AREA

An AssetType defines or references the properties that are meaningful for that category.

## 6. AssetProperty

A typed property associated with an asset.

Examples:

- tree.species = "Quercus robur"
- tree.height = 18 m
- tree.age = 42 years
- pond.surface = 1200 m²
- business.employees = 35

Properties may be unknown.

The model should support units and metadata.

## 7. Scenario

Represents a specific project intervention or future state.

A project may eventually contain multiple scenarios.

Examples:

- Existing situation
- Proposed development
- Alternative A
- Alternative B

## 8. Intervention

Represents a project-specific modification of the territory.

Possible intervention states include:

- REMOVE
- ADD
- MODIFY
- MOVE
- AFFECT

An intervention must reference the project/scenario and the relevant asset.

## 9. Dependency

Represents a meaningful relationship through which a change affecting one entity may influence another.

Main conceptual attributes:

- id
- source_asset_id
- target_asset_id
- dependency_type_id
- direction
- strength
- distance_or_scope
- evidence
- confidence
- created_at

A dependency should not be interpreted automatically as a causal relationship unless its semantics explicitly support causality.

## 10. DependencyType

Defines the semantic nature of a dependency.

Initial families may include:

### Geographic

- proximity
- neighbourhood
- wind corridor
- runoff
- exposure
- accessibility

### Economic

- supplier
- customer
- employment
- economic flow

### Social

- attraction
- repulsion
- accessibility
- usage
- social interaction

### Environmental

- habitat
- pollination
- cooling
- water regulation
- air purification
- biodiversity interaction

The taxonomy must remain extensible.

## 11. EcosystemService

Represents a documented service provided by an ecosystem or natural asset.

Examples:

- air purification;
- carbon storage;
- water retention;
- thermal regulation;
- noise reduction;
- biodiversity support;
- recreational benefit;
- mental-health-related benefit.

An EcosystemService is a scientific/domain concept, not merely a numerical value.

## 12. Reference

Represents a source supporting a model, parameter, empirical relationship or conversion.

Possible source types:

- scientific paper;
- governmental reference;
- institutional dataset;
- technical report;
- local study.

References must be stored explicitly to support traceability.

## 13. ValuationModel

Defines a documented method for transforming measurable effects into a quantitative or monetary value.

A valuation model must specify:

- inputs;
- units;
- equations or transformation rules;
- assumptions;
- source references;
- output unit;
- uncertainty where available.

## 14. Analysis

Represents a computation performed for a project/scenario.

An analysis should preserve:

- input scenario;
- selected propagation depth;
- selected dependency types;
- models used;
- reference versions;
- date of computation;
- resulting entities/effects;
- assumptions.

The purpose is reproducibility.
