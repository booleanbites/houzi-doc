---
title: Map View Initial Location Hook
category: Hooks & Widgets
permalink: hooks-widgets/map_view_initial_location_hook
order: 347
---

Houzi provides the **`getMapViewInitialLocationHook()`** to set the **initial/default center location and zoom level** of the map view when it first loads, before any property markers are displayed.

## When to Use

Use this hook when you want to control where the map is centered on initial load. This is useful if your properties are concentrated in a specific region and you want the map to open directly on that area instead of the default location.

## How to Use

Open `hooks_v2.dart` and locate the **`getMapViewInitialLocationHook()`** method. If not available then copy and paste the code from here.

1. Set the `latitude` and `longitude` values to your desired initial map center.
2. Set the `initial_zoom` value to control how zoomed in the map should be on load.
3. Return the map from the function.

```dart
@override
MapViewInitialLocationHook getMapViewInitialLocationHook() {
  MapViewInitialLocationHook mapViewInitialLocationHook = () {

    /// Return a Map with 'latitude' and 'longitude' keys to set the
    /// initial/default center of the map view.
    /// These coordinates will be used when the map first loads,
    /// before any property markers are shown.

    Map<String, dynamic> initialLocationMap = {
      "latitude": 37.4219999,
      "longitude": -122.0862462,
      "initial_zoom": 8.0,
    };

    return initialLocationMap;
  };
  return mapViewInitialLocationHook;
}
```

## Map Keys

| Key | Type | Description |
|---|---|---|
| `latitude` | `double` | Latitude of the initial map center |
| `longitude` | `double` | Longitude of the initial map center |
| `initial_zoom` | `double` | Initial zoom level of the map (e.g., `8.0` for region-level, `12.0` for city-level) |

## Usage Example

```dart
@override
MapViewInitialLocationHook getMapViewInitialLocationHook() {
  MapViewInitialLocationHook mapViewInitialLocationHook = () {
    Map<String, dynamic> initialLocationMap = {
      "latitude": 25.2048,
      "longitude": 55.2708,
      "initial_zoom": 10.0,
    };
    return initialLocationMap;
  };
  return mapViewInitialLocationHook;
}
```

> After modifications, restart the app and the changes will reflect in your app.