---
title: Houzi Map Provider Hook
category: Hooks & Widgets
permalink: hooks-widgets/houzi_map_provider_hook
order: 345
---

Houzi provides the **`getHouziMapProviderHook()`** to let you **set the default map provider** used throughout the app. You can choose between **Google Maps** and **OpenStreetMap (OSM)**.

## When to Use

Use this hook when you want to override the default map provider set by Houzi. By default, Houzi uses **OpenStreetMap (OSM)** as the map provider. If your app requires **Google Maps**, you can switch to it using this hook.

## How to Use

Open `hooks_v2.dart` and locate the **`getHouziMapProviderHook()`** method.
If not available then copy and paste the code from here.

1. Return `"google"` to use **Google Maps**.
2. Return `"osm"` to use **OpenStreetMap**.
3. Return `""` (empty string) to use the **default map provider** set by Houzi (which is OSM).

```dart
@override
HouziMapProviderHook getHouziMapProviderHook() {
  HouziMapProviderHook houziMapProviderHook = () {
    /// Use this hook to set the default map provider.
    ///
    /// We have two map providers to use:
    /// 1. Return "google" for Google Maps.
    /// 2. Return "osm" for OpenStreetMap.
    ///
    /// Example is below map to use Google Maps
    /// Uncomment the below line to use Google Maps
    // return "google";

    /// Example is below map to use OpenStreetMap
    /// Uncomment the below line to use OpenStreetMap
    // return "osm";

    /// Return empty incase to use default map provider set by Houzi which is OSM
    return "";
  };
  return houziMapProviderHook;
}
```

## Usage Examples

### Example 1: Using Google Maps

```dart
@override
HouziMapProviderHook getHouziMapProviderHook() {
  HouziMapProviderHook houziMapProviderHook = () {
    return "google";
  };
  return houziMapProviderHook;
}
```

### Example 2: Using OpenStreetMap

```dart
@override
HouziMapProviderHook getHouziMapProviderHook() {
  HouziMapProviderHook houziMapProviderHook = () {
    return "osm";
  };
  return houziMapProviderHook;
}
```

> **Note:** If you choose to use **OpenStreetMap (OSM)**, you **must** provide a valid admin email address using the **OSM Geo Admin Email Hook**. Please refer to the [OSM Geo Admin Email Hook](/hooks-widgets/osm_geo_admin_email_hook) documentation to set it up.

> After modifications, restart the app and the changes will reflect in your app.