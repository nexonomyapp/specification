# Nexonomie — API and Backend Principles

## 1. Purpose

This document describes backend principles rather than prescribing a specific framework.

## 2. Backend as source of truth

The backend/database must be authoritative for:

- users;
- projects;
- assets;
- scenarios;
- dependencies;
- references;
- analyses.

The frontend should not contain authoritative business logic.

## 3. Business logic

Important domain operations should be implemented in reusable backend services/functions.

Examples:

```text
createScenario()
addIntervention()
findAffectedAssets()
propagateDependencies()
estimateEcosystemService()
runAnalysis()
```

The exact implementation language is not prescribed.

## 4. Geographic queries

The backend should support spatial operations such as:

- assets inside an area;
- assets intersecting an area;
- assets within a radius;
- nearest assets;
- spatial filtering.

These operations should be performed using appropriate geographic database capabilities rather than downloaded entirely to the browser.

## 5. Graph queries

Dependency traversal should be implemented server-side when the graph becomes large.

The API should support queries such as:

```text
getDirectDependencies(asset_id)
getDependencies(asset_id, depth)
findPaths(source, target)
getAffectedAssets(scenario_id, depth)
```

## 6. Analysis execution

A nexonomic analysis should be represented as an explicit operation.

Conceptually:

```text
POST /analysis
```

with:

```text
project
scenario
propagation parameters
dependency filters
model versions
```

The returned Analysis object becomes a reproducible record of the computation.

## 7. Idempotence

Where possible, repeated execution with identical inputs should produce identical results.

## 8. Audit trail

Important modifications should eventually be auditable.

At minimum:

- user;
- timestamp;
- object;
- operation;
- previous value;
- new value.

## 9. Validation

Backend validation must enforce:

- required fields;
- valid enumerations;
- compatible geometry types;
- valid units;
- project permissions;
- dependency consistency.

## 10. Transactions

Operations that modify several related records should be atomic where possible.

For example, creating an intervention should not leave the database in a partially created state.

## 11. Computed results

Computed analysis results should not overwrite source data.

The source data and computed analysis must remain separate.

## 12. API evolution

The API should be designed so that future versions can evolve without silently breaking existing analyses.

## 13. External data

External services may provide:

- map tiles;
- geographic datasets;
- geocoding;
- scientific references;
- other public information.

External data must retain provenance.

## 14. AI services

AI may assist with:

- classification;
- extraction;
- suggestion of dependencies;
- summarisation;
- interface assistance.

AI-generated results must be explicitly marked and must not silently become validated scientific knowledge.

## 15. Security

All project-specific operations must be authorized server-side.

Never rely solely on frontend visibility to protect data.
