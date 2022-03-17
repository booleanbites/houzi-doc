---
title: Showing feature icon in property details
category: App Setup
order: 7
---

If you want to show feature icon for your translated property feature, you need to open following file:

` Project_HOME > packages > houzi_package > lib > pages > property_details_page.dart`

Then look for _iconMap, and edit existing or add new entry for your desired features, eg: 
```
Map<String, dynamic> _iconMap = {
    "Piscine": Icons.pool_outlined, 
    "Pool": Icons.pool_outlined,
    ...
};
```
The Icons.xxxxx are coded from Google Material icons here:
https://fonts.google.com/icons
