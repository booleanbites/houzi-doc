---
title: Feature icon in Property Details
category: Hooks & Widgets
permalink: hooks-widgets/property_details_feature_icons
order: 314
---

If you want to show feature icon for your translated property feature, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getPropertyDetailPageIconsMap()` method. Then look for _iconMap, and edit existing or add new entry for your desired features, eg: 
```dart
Map<String, dynamic> _iconMap = {
    "Piscine": Icons.pool_outlined, 
    "Pool": Icons.pool_outlined,
    ...
};
```
The Icons.xxxxx are coded from Google Material icons here:
https://fonts.google.com/icons
