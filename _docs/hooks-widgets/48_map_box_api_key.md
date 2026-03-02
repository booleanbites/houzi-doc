---
title: Map Box Api Key Hook
category: Hooks & Widgets
permalink: hooks-widgets/map_box_api_key_hook
order: 348
---

Houzi provides the **`getMapBoxApiKeyHook()`** to set the **Mapbox API key** for Mapbox services in the app.

## When to Use

Use this hook when you want to use Mapbox services in the app.

## How to Use

Open `hooks_v2.dart` and locate the **`getMapBoxApiKeyHook()`** method. If not available then copy and paste the code from here.

1. Set the `map_box_api_key` value to your desired Mapbox API key.
2. Return the map from the function.

```dart
@override
  MapBoxApiKeyHook getMapBoxApiKeyHook() {
    MapBoxApiKeyHook mapBoxApiKeyHook = () {

      /// Return your Mapbox Access Token if you are using Mapbox as the map provider.
      /// Required for loading Mapbox tiles, styles, geocoding, and reverse geocoding services.
      /// You can generate your access token from the Mapbox Dashboard:
      /// https://account.mapbox.com/
      /// Example: "pk.xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.abcdefghijklmnopqrstuvwxyz"
      /// Not needed if using Google Maps or OpenStreetMap only.
      ///
      /// Leave empty if you are using Google Maps or OpenStreetMap only.

      return "";
    };
    return mapBoxApiKeyHook;
  }
```

## Usage Example

```dart
@override
MapBoxApiKeyHook getMapBoxApiKeyHook() {
  MapBoxApiKeyHook mapBoxApiKeyHook = () {
    /// Example Key: "pk.xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.abcdefghijklmnopqrstuvwxyz"
    /// Replace with your Mapbox Access Token
    return "YOUR_MAPBOX_API_KEY";
  };
  return mapBoxApiKeyHook;
}
```

> After modifications, restart the app and the changes will reflect in your app.
