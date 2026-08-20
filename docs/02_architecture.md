# Nexonomie — Conceptual Architecture

## 1. Architectural layers

The application should be designed as several logically separated layers.

### Layer A — Application

Responsible for:

- authentication;
- projects;
- navigation;
- user interface;
- permissions.

### Layer B — Territorial model

Responsible for:

- maps;
- study areas;
- geographic assets;
- asset types;
- asset properties;
- geographic metadata.

### Layer C — Scenario model

Responsible for:

- interventions;
- removed assets;
- modified assets;
- added assets;
- project-specific effects.

### Layer D — Dependency model

Responsible for:

- dependencies;
- dependency types;
- directions;
- strength or intensity;
- evidence;
- graph traversal;
- propagation depth.

### Layer E — Scientific knowledge

Responsible for:

- ecosystem services;
- scientific references;
- parameters;
- empirical relationships;
- conversion models;
- assumptions;
- uncertainty.

### Layer F — Analysis and valuation

Responsible for:

- propagation results;
- quantified effects;
- temporal aggregation;
- economic valuation;
- synthesis;
- reporting.

## 2. Separation of concerns

The application must not confuse an entity with its role in a particular project.

For example, an existing tree is a territorial asset. The fact that a particular project removes that tree belongs to the project scenario, not to the collective definition of the tree.

Likewise, a scientific model describing the cooling service of trees is not a property of an individual tree. It belongs to the scientific reference layer and is applied to the tree using its parameters.

## 3. Desired technical direction

The precise technology may evolve, but the conceptual architecture should support:

- relational persistent data;
- geographic geometries;
- typed properties;
- graph-like relationships;
- versionable scientific references;
- auditable calculations;
- user/project permissions;
- external APIs where appropriate.

The implementation should avoid hard-coding domain categories into the core application whenever possible.

## 4. Extensibility

The system must allow new:

- asset types;
- properties;
- dependency types;
- ecosystem services;
- reference datasets;
- valuation models;

to be added without redesigning the entire application.

This is essential because the Nexonomie ontology will evolve as the methodology develops.
