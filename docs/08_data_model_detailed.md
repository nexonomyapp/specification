# Nexonomie — Detailed Data Model v0.1

This document refines the conceptual model into a structure suitable for implementation.

## 1. General principles

The data model must distinguish four categories of information:

1. **Territorial data** — reusable facts about assets and their location.
2. **Project data** — information specific to a study.
3. **Scientific knowledge** — references, parameters and models.
4. **Computed analysis data** — results produced by an analysis.

These categories must not be silently merged.

## 2. Core entities

### User

```text
User
- id
- email
- display_name
- created_at
- updated_at
```

### Project

```text
Project
- id
- name
- description
- owner_id
- status
- created_at
- updated_at
```

### StudyArea

```text
StudyArea
- id
- project_id
- name
- geometry
- geometry_type
- crs
- created_at
- updated_at
```

A project may eventually contain several study areas, even if the first implementation uses one.

### Asset

```text
Asset
- id
- asset_type_id
- name
- description
- geometry
- geometry_type
- properties
- provenance
- created_at
- updated_at
```

Assets are reusable territorial objects.

### AssetType

```text
AssetType
- id
- code
- name
- description
- icon
- geometry_types
- property_schema
```

`code` should be stable and machine-readable.

Example:

```text
TREE
BUILDING
BUSINESS
POND
FOREST
ROAD
```

## 3. Project-specific entities

### ProjectAsset

A ProjectAsset links an existing Asset to a Project without copying the asset itself.

```text
ProjectAsset
- id
- project_id
- asset_id
- relevance
- notes
- added_at
```

This permits the same territorial asset to participate in several studies.

### Scenario

```text
Scenario
- id
- project_id
- name
- description
- status
- created_at
- updated_at
```

### Intervention

```text
Intervention
- id
- scenario_id
- asset_id
- action
- geometry_before
- geometry_after
- properties_before
- properties_after
- notes
- confidence
```

Possible actions:

```text
REMOVE
ADD
MODIFY
MOVE
AFFECT
```

For `ADD`, `asset_id` may refer to a newly created scenario asset or a scenario-local entity.

## 4. Dependency entities

### DependencyType

```text
DependencyType
- id
- code
- name
- family
- description
- directed
```

### Dependency

```text
Dependency
- id
- source_asset_id
- target_asset_id
- dependency_type_id
- direction
- strength
- confidence
- spatial_scope
- temporal_scope
- evidence
- provenance
- status
- created_at
- updated_at
```

The dependency is directed conceptually:

```text
source → target
```

meaning that a change affecting the source may influence the target.

The direction must not automatically be interpreted as causal unless the dependency type explicitly defines causality.

## 5. Scientific knowledge

### Reference

```text
Reference
- id
- title
- authors
- year
- publisher
- url
- identifier
- reference_type
- citation
```

### ParameterDefinition

```text
ParameterDefinition
- id
- code
- name
- description
- unit
- data_type
- default_value
- uncertainty_description
```

### ScientificModel

```text
ScientificModel
- id
- code
- name
- description
- model_type
- formula_or_method
- output_unit
- assumptions
- version
- status
```

A ScientificModel may reference several References and ParameterDefinitions.

## 6. Ecosystem services

### EcosystemService

```text
EcosystemService
- id
- code
- name
- category
- description
- output_unit
```

### ServiceModel

A ServiceModel defines how an asset's properties are transformed into an estimate of an ecosystem service.

```text
ServiceModel
- id
- ecosystem_service_id
- scientific_model_id
- input_schema
- output_unit
- assumptions
- version
```

## 7. Analysis

### Analysis

```text
Analysis
- id
- project_id
- scenario_id
- name
- propagation_depth
- dependency_filters
- model_versions
- created_at
- status
```

### AnalysisNode

Stores the participation of an asset in a particular analysis.

```text
AnalysisNode
- id
- analysis_id
- asset_id
- distance_from_intervention
- inclusion_reason
- status
```

### AnalysisPath

Stores a dependency path explaining propagation.

```text
AnalysisPath
- id
- analysis_id
- source_asset_id
- target_asset_id
- path
- path_length
- relevance
```

## 8. Results

Results should be separated from source data.

```text
AnalysisEffect
- id
- analysis_id
- asset_id
- effect_type
- quantity
- unit
- annual_value
- cumulative_value
- confidence
- model_id
- explanation
```

## 9. Important implementation rule

Do not store computed values as if they were intrinsic asset properties.

For example:

```text
WRONG:
Tree.cooling_value = 430 €/year
```

Prefer:

```text
Asset
  + properties

ScientificModel
  + parameters

Analysis
  + computed effect
```

The same tree may have different results depending on the scenario, model version or assumptions.
