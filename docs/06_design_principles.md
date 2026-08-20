# Nexonomie — Design Principles

## 1. Explainability before automation

An automatically generated result must remain inspectable.

The user should be able to determine:

- which assets contributed;
- which dependencies were used;
- which scientific models were applied;
- which parameters were used;
- which references support the calculation.

## 2. Data provenance

Whenever data originates from an external source, preserve its provenance.

The system should distinguish:

- user-provided information;
- collectively maintained information;
- imported geographic information;
- scientific reference data;
- automatically inferred information.

## 3. Collective data vs project data

This distinction is fundamental.

### Collective

Facts about the territory and reusable assets.

### Project-specific

Facts about what a particular project does to those assets.

A project must never silently alter collective territorial information.

## 4. Unknown is not zero

An unavailable value must not automatically be interpreted as zero.

For example:

- unknown tree age ≠ age 0;
- unknown number of employees ≠ 0 employees;
- unknown biodiversity ≠ no biodiversity.

The data model must support missing information explicitly.

## 5. Preserve units

Every quantitative parameter should have an explicit unit where applicable.

Examples:

- m
- m²
- kg
- kWh
- €/year
- employees
- years

Unit conversion must be explicit and documented.

## 6. Avoid hidden assumptions

If a calculation requires an assumption, expose it.

The system should distinguish measured values, estimated values, default values and assumptions.

## 7. Avoid premature aggregation

Keep effects separate for as long as possible.

For example, thermal regulation, carbon storage and health effects should not be immediately collapsed into one number.

Aggregation should occur only when the semantics justify it.

## 8. Prevent double counting

The future valuation engine must explicitly address overlapping effects.

A benefit should not be counted twice simply because it appears through two dependency paths.

## 9. Human validation

Automatically inferred dependencies and effects should be distinguishable from manually validated ones.

The user should be able to inspect, accept, reject or modify automatically generated relationships when appropriate.

## 10. Scientific references are first-class objects

Scientific sources should not be buried in free text.

References should be reusable, searchable and attached to the models or parameters they support.

## 11. Progressive complexity

The user interface should initially show the simplest meaningful information and reveal deeper layers on demand.

The application must remain usable even when a project contains thousands of assets and dependencies.

## 12. Reproducibility

A computed analysis should be reproducible from its stored inputs, model versions, references and parameters.

## 13. No invented scientific knowledge

The application and its AI-assisted development process must never silently invent scientific parameters, empirical relationships or valuation coefficients.

Where scientific information is missing, the system should explicitly mark the corresponding element as undefined, estimated, or requiring a source.
