---
title: Showing feature icon in property details
category: Custom Widgets
order: 5
---

If you want to show feature icon for your translated property feature, you need to open following file:

`Project_HOME  > lib > Hooks.dart`

Look for the `getPropertyDetailPageIconsMap()` method. Then look for _iconMap, and edit existing or add new entry for your desired features, eg: 
```
Map<String, dynamic> _iconMap = {
    "Piscine": Icons.pool_outlined, 
    "Pool": Icons.pool_outlined,
    ...
};
```
The Icons.xxxxx are coded from Google Material icons here:
https://fonts.google.com/icons
