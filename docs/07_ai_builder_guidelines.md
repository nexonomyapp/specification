# Nexonomie — AI Builder Development Guidelines

This document is intended for AI development agents such as Base44, Lovable, or other coding agents.

## 1. Repository as source of truth

Before implementing a feature:

1. inspect the repository;
2. identify relevant domain concepts;
3. inspect existing data models;
4. inspect existing functionality;
5. preserve established terminology and relationships.

Do not redesign the application's conceptual model without explicit instruction.

## 2. Incremental implementation

Implement one functional block at a time.

For each block:

1. understand the requested functionality;
2. inspect existing code;
3. modify the smallest necessary set of components;
4. preserve existing functionality;
5. test the new behaviour;
6. report what was changed.

Do not implement future roadmap items unless explicitly requested.

## 3. Data model discipline

Before creating a new database object, check whether an existing concept already represents it.

Avoid duplicate concepts such as:

- Entity vs Asset;
- ProjectArea vs StudyArea;
- Relation vs Dependency.

Use the terminology defined in `05_terminology.md`.

## 4. UI discipline

The application should have a coherent modern visual language.

Prefer:

- clear information hierarchy;
- restrained visual design;
- generous spacing;
- map-first workflows where appropriate;
- contextual inspectors;
- progressive disclosure;
- responsive layouts.

Avoid:

- unnecessary dashboards;
- excessive cards;
- decorative animations;
- dense forms;
- exposing technical database terminology to ordinary users.

## 5. Geographic discipline

All geographic objects must have explicit geometry semantics.

Do not silently mix:

- points;
- lines;
- polygons;
- administrative boundaries;
- study areas;
- intervention areas.

Preserve the coordinate reference information when relevant.

## 6. Scientific discipline

Never fabricate:

- scientific coefficients;
- economic values;
- epidemiological relationships;
- ecosystem-service estimates;
- conversion factors;
- references.

If a required scientific value is not available, create a placeholder configuration that clearly states that a validated source is required.

## 7. Calculation discipline

Calculations must be deterministic given the same inputs and model version.

Store enough metadata to reconstruct the calculation.

## 8. Security and permissions

Project-specific data must respect project permissions.

Collective asset data and project scenario data must not be confused from a permissions perspective.

## 9. Backward compatibility

Do not break existing projects when adding new functionality.

When changing the database schema, provide an appropriate migration or compatibility mechanism.

## 10. AI-generated code

Generated code must be treated as ordinary production code.

Prefer simple, maintainable implementations over clever abstractions.

Do not add dependencies unless they provide a clear benefit.

## 11. Before each implementation

The AI agent should summarize:

- which repository documents are relevant;
- which existing components will be reused;
- which data structures will change;
- which new functionality will be added.

Then implement only the requested block.

## 12. Completion criterion

A feature is complete only when:

- it works through the user interface;
- data persists correctly;
- existing functionality remains operational;
- obvious error states are handled;
- terminology is consistent with the repository;
- the implementation does not silently introduce unsupported scientific assumptions.
