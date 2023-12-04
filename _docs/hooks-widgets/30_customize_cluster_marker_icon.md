---
title: Customize Cluster Marker Icon
category: Hooks & Widgets
permalink: hooks-widgets/customize_cluster_marker_icon
order: 330
---

If you want to customize the cluster marker on Google Maps, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getCustomizeClusterMarkerIconHook()` method. You can modify the cluster icon colors as well as its size. You are provided with the **clusterMarkerDataMap**. Provide your releted customization against the respective key and return the *clusterMarkerDataMap* instead of returning *null*. 

After modifications, restart the app and the changes will reflect on Maps.

```dart
@override
  ClusterMarkerIconHook getCustomizeClusterMarkerIconHook() {
    ClusterMarkerIconHook customizedClusterMarkerIconHook = () {
      Map<String, dynamic>? clusterMarkerDataMap = {
        "clusterColor": Colors.blue,
        "clusterTextColor": Colors.white,
        "clusterBorderColor": Colors.white,
        "clusterWidth": 80, // int
        "clusterBorderWidth": 10.0, // double
      };

      // return clusterMarkerDataMap;
      return null;
    };

    return customizedClusterMarkerIconHook;
  }
```

> **Note**: If you want to show the Cluster Marker Icon with default settings, return null.

*Added in version 1.3.8*

