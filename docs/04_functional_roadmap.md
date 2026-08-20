# Nexonomie — Functional Roadmap

The application should be built in the following order.

## Phase 1 — Application foundation

### F01 — Authentication
Users can create an account and log in.

### F02 — Projects
Users can create, open, edit and delete projects.

### F03 — Project workspace
A project has a dedicated workspace with navigation.

## Phase 2 — Territory

### F04 — Interactive map
Display an interactive geographic map.

### F05 — Study area
Allow the user to draw and edit the study/intervention area.

### F06 — Asset display
Display known assets on the map.

### F07 — Asset creation
Allow users to create new assets.

### F08 — Asset inspector
Display and edit asset properties.

## Phase 3 — Project scenario

### F09 — Existing assets
Identify assets already present in the study area.

### F10 — Removed assets
Mark assets that will be removed by the project.

### F11 — Added assets
Define assets that will exist after the project.

### F12 — Modified assets
Represent assets whose state changes without being removed.

The scenario information must remain project-specific.

## Phase 4 — Dependencies

### F13 — Dependency data model
Represent directed and typed dependencies.

### F14 — Manual dependencies
Allow users to create or edit dependencies when appropriate.

### F15 — Automatic dependencies
Generate candidate dependencies from geographic or domain rules.

### F16 — Dependency explorer
Explore the neighbours of an asset.

### F17 — Propagation
Expand the set of affected assets to a configurable depth.

## Phase 5 — Graph

### F18 — Dependency graph
Display assets as nodes and dependencies as edges.

### F19 — Interactive graph exploration
Allow filtering, expansion, collapsing and inspection.

### F20 — Map/graph synchronisation
Selecting an asset on the map highlights it in the graph and vice versa.

## Phase 6 — Scientific knowledge

### F21 — Asset-type catalogue
Manage categories and properties.

### F22 — Ecosystem-service catalogue
Manage documented ecosystem services.

### F23 — Scientific references
Store and display sources.

### F24 — Parameters and models
Define reusable scientific parameters and equations.

## Phase 7 — Quantification

### F25 — Service estimation
Estimate service intensity for an asset.

### F26 — Conversion chains
Transform service quantities through documented conversion steps.

### F27 — Economic valuation
Produce annual or cumulative monetary values.

### F28 — Temporal modelling
Represent duration, evolution and lifetime.

### F29 — Uncertainty
Represent uncertainty and confidence where possible.

## Phase 8 — Nexonomic analysis

### F30 — Analysis engine
Compute the network of potentially affected entities.

### F31 — Effect propagation
Track effects through dependency paths.

### F32 — Aggregation
Aggregate compatible effects while controlling for double counting.

### F33 — Nexonomic synthesis
Produce a structured interpretation of direct and indirect effects.

### F34 — Nexonomic cost
Compute the final nexonomic valuation once the methodology has been formally specified.

## Rule

Do not implement a later phase merely because it is conceptually described.

Each phase should be implemented only after its preceding data model and user workflow are stable.
