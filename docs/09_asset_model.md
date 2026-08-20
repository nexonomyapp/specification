# Nexonomie — Asset Model

## 1. Definition

An Asset is a geographically identifiable entity that can participate in a nexonomic analysis.

Examples include:

- tree;
- group of trees;
- forest;
- pond;
- hedge;
- park;
- building;
- dwelling;
- business;
- road;
- agricultural parcel;
- public facility.

The Asset model must remain generic.

## 2. Geometry

An Asset may have:

- Point geometry;
- Line geometry;
- Polygon geometry;
- Multi-geometry where required.

Examples:

```text
TREE       → Point
ROAD       → Line
BUILDING   → Polygon
FOREST     → Polygon
```

The geometry is part of the territorial identity of the asset.

## 3. Properties

Properties are typed values associated with an AssetType.

Example:

```text
Tree
├── species: string
├── height: number [m]
├── diameter: number [cm]
├── age: number [years]
├── health_status: categorical
└── canopy_area: number [m²]
```

The property system should support:

- strings;
- numbers;
- booleans;
- dates;
- enumerations;
- quantities with units;
- references to other assets.

## 4. Unknown values

Unknown values must be represented explicitly.

The system should distinguish:

```text
known value
unknown
not applicable
estimated
default
```

Do not convert missing data into zero.

## 5. Provenance

Each important property should eventually be able to indicate where it came from.

Possible provenance:

```text
USER
OPEN_DATA
IMPORTED_DATASET
AUTOMATIC_INFERENCE
SCIENTIFIC_REFERENCE
LOCAL_SURVEY
```

## 6. Asset identity

An Asset must have a stable identifier independent of its display name.

Names may change.

The identifier must not.

## 7. Collective assets

Assets may be visible to multiple projects.

The collective asset record contains territorial information.

Project-specific information belongs to ProjectAsset, Scenario or Intervention.

## 8. Asset lifecycle

Assets may be:

- active;
- archived;
- superseded.

Deletion should be avoided where historical analyses depend on the asset.

## 9. Asset categories

The initial taxonomy should be deliberately small.

Suggested initial categories:

### Natural

- TREE
- FOREST
- HEDGE
- POND
- PARK
- AGRICULTURAL_AREA

### Built

- BUILDING
- DWELLING
- PUBLIC_FACILITY
- ROAD
- INFRASTRUCTURE

### Economic

- BUSINESS
- SHOP
- INDUSTRIAL_SITE

The taxonomy should later be expanded through configuration rather than code changes.

## 10. References between assets

Some asset properties are naturally relational.

Examples:

```text
Business → supplier → Business
Business → customer → Business
Building → contains → Dwelling
Park → contains → Tree
Road → serves → Building
```

These should normally be represented as Dependencies or domain relations rather than arbitrary JSON fields.

## 11. Asset inspector

The user-facing inspector should present:

1. identity;
2. location;
3. category;
4. properties;
5. provenance;
6. project participation;
7. dependencies;
8. ecosystem services;
9. analysis results.

The inspector should reveal advanced information progressively.
