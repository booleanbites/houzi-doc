---
title: Custom Cluster Marker Icon
category: Hooks & Widgets
permalink: hooks-widgets/custom_cluster_marker_icon
order: 331
---

If you want to display your custom cluster marker on Google Maps, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getCustomClusterMarkerIconHook()` method. You are provided with the **customClusterMarkerIconHook** with 2 additional parameters i.e. BuildContext and clusterSize. Define your cluster marker icon here and return it instead of returning *null*. 

After modifications, restart the app and the changes will reflect on Maps.

```dart
@override
  CustomClusterMarkerIconHook getCustomClusterMarkerIconHook() {
    CustomClusterMarkerIconHook customClusterMarkerIconHook = (BuildContext context, int clusterSize) {

      return null;
    };

    return customClusterMarkerIconHook;
  }
```

> **Note**: If you want to show the Default Cluster Marker Icon, return null.

*Added in version 1.3.8*

