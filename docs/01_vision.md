# Nexonomie — Vision

## 1. Purpose

Nexonomie is intended to help a professional understand the systemic consequences of a territorial or urban-development project.

A conventional project analysis often focuses on direct effects: which buildings disappear, which roads are modified, which land is occupied, or which infrastructures are constructed.

A nexonomic analysis extends this view by asking:

> Which other entities depend on these entities, directly or indirectly, and what effects can propagate through these dependencies?

The platform therefore combines geographical representation, entity modelling, dependency networks, scientific references and quantitative valuation.

## 2. Core conceptual chain

The conceptual workflow is:

**Project → Intervention → Directly affected entities → Dependencies → Propagation → Effects → Valuation**

The application should make this chain visible and explorable.

A user should be able to start from a concrete territorial intervention and progressively understand increasingly indirect consequences.

## 3. Main objects

The central concepts are:

- Project
- Study Area
- Asset / Entity
- Asset Type
- Scenario
- Intervention
- Dependency
- Dependency Type
- Effect
- Ecosystem Service
- Reference
- Valuation Model
- Analysis

These concepts should remain distinct even when the user interface presents them together.

## 4. Product vision

The final application should feel like a combination of:

- a GIS application;
- an asset/entity inspector;
- a dependency graph explorer;
- a scientific knowledge base;
- a quantitative analysis environment.

The interface should remain understandable to a non-programmer.

## 5. Important distinction

Nexonomie is not initially a monetary valuation tool.

The monetary valuation is the final layer.

The first objective is to construct a reliable representation of the territory and its network of dependencies. Quantification must be explainable and traceable back to the entities, relationships, parameters and scientific references from which it was derived.

## 6. Explainability

Every significant computed result should eventually be explainable.

For example, a result such as:

> Estimated annual loss: €X/year

should ultimately be traceable through a chain such as:

**Project → removed tree → cooling service → estimated cooling capacity → equivalent energy consumption → annual economic value**

The application should avoid opaque calculations wherever possible.
