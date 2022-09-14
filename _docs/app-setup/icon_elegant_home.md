---
title: Showing term icon in home
category: App Setup
order: 8
---

If you want to show term icon for your translated term, you need to open following file:

`Project_HOME  > lib > Hooks.dart`

Look for the `getElegantHomeTermsIconMap()` method. Then look for _iconMap, and edit existing or add new entry for your desired term, add the slug-name of your term eg: 
```
Map<String, dynamic> _iconMap = {
     "for-rent": Icons.vpn_key_outlined,
     "residential": Icons.apartment_outlined;
    ...
};
```
The Icons.xxxxx are coded from Google Material icons here:
https://fonts.google.com/icons
