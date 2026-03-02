---
title: OSM Geo Admin Email Hook
category: Hooks & Widgets
permalink: hooks-widgets/osm_geo_admin_email_hook
order: 346
---

Houzi provides the **`getOsmGeoAdminEmailHook()`** to set a **valid admin email address** required by OpenStreetMap's Nominatim service for geocoding (search and reverse geocoding) requests.

## When to Use

This hook is **required** when you are using **OpenStreetMap (OSM)** as your map provider. Nominatim requires a valid contact email for identification purposes as part of its [usage policy](https://operations.osmfoundation.org/policies/nominatim/).

> **Important**  
> If you have set your map provider to `"osm"` using the [Houzi Map Provider Hook](/hooks-widgets/houzi_map_provider_hook), you **must** configure this hook with a valid email address. Without it, your geocoding requests may be blocked by the Nominatim service.

> **Note:** This hook is **not needed** if you are using **Google Maps** only.

## How to Use

Open `hooks_v2.dart` and locate the **`getOsmGeoAdminEmailHook()`** method. If not available then copy and paste the code from here.

1. Replace the example email with your **valid admin/support email**.
2. Return the email string from the function.

```dart
@override
OSMGeoAdminEmailHook getOsmGeoAdminEmailHook() {
  OSMGeoAdminEmailHook osmGeoAdminEmailHook = () {

    /// Return a valid admin email for OpenStreetMap (Nominatim) Search/Reverse.
    /// Required by OSM for identification and contact purposes.
    /// Example: "support@yourapp.com"
    /// Not needed if using Google Maps only.

    return "support@yourapp.com";
  };
  return osmGeoAdminEmailHook;
}
```

## Usage Example

```dart
@override
OSMGeoAdminEmailHook getOsmGeoAdminEmailHook() {
  OSMGeoAdminEmailHook osmGeoAdminEmailHook = () {
    return "admin@myrealestate.com";
  };
  return osmGeoAdminEmailHook;
}
```

> After modifications, restart the app and the changes will reflect in your app.