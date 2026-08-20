# Nexonomie — Map Requirements

## 1. Purpose

The map is the primary spatial interface of Nexonomie.

It must combine geographic context, study boundaries, assets and scenario information.

## 2. Base map

The first version should support an open geographic base layer such as OpenStreetMap.

The architecture should allow additional layers later, including authoritative public geographic datasets where licensing and access conditions permit.

## 3. Study area

The user must be able to:

- create a polygon;
- edit vertices;
- move vertices;
- delete the area;
- save the geometry.

The geometry must be stored independently from the visual map.

## 4. Intervention area

The application should distinguish the broader Study Area from the precise Intervention Area.

The Intervention Area may be used to identify candidate directly affected assets.

## 5. Assets on map

Assets should be represented according to their AssetType.

Examples:

```text
TREE       → tree marker
BUILDING   → building geometry
FOREST     → polygon
ROAD       → line
BUSINESS   → business marker
```

The exact visual language should remain configurable.

## 6. Asset interaction

Clicking an asset should:

1. highlight it;
2. open or focus the asset inspector;
3. show its basic properties;
4. provide access to its dependencies.

## 7. Scenario visualization

The map should distinguish:

- existing assets;
- assets marked for removal;
- modified assets;
- newly added assets;
- assets discovered indirectly by analysis.

These states must be visually distinguishable without relying only on colour.

## 8. Layers

The architecture should support future layers such as:

- cadastral boundaries;
- zoning;
- flood risk;
- wind;
- vegetation;
- transport;
- noise;
- environmental constraints.

Layers should be independently togglable.

## 9. Spatial filtering

The user should eventually be able to filter assets by:

- category;
- distance;
- project status;
- scenario status;
- dependency status.

## 10. Performance

The map must remain usable with large numbers of assets.

Clustering, spatial indexing or progressive loading may be required.

## 11. Map/inspector synchronisation

The map and inspector must represent the same selected asset.

Selecting an asset in one should update the other.

## 12. Map/graph synchronisation

Later, selecting an asset in the dependency graph should center and highlight the corresponding asset on the map.
