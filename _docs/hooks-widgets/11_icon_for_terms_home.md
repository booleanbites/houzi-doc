---
title: Set icon for Terms on Home
category: Hooks & Widgets
permalink: hooks-widgets/term_icon_item_design_custom
order: 311
---

Each Property Type, Property Status and Property Label are called Term in the Houzez (wordpress) taxonomies. When you add a new property type, you actually add new term in Property Type taxonomy in your wordpress.

When you open app, the app loads Property Type, Property Status and other taxonomies on homepage. For each term (for-sale, for-rent, house, office) we show an icon against its slug. See below screenshot

![Houzi home term icon](../../images/houzi-home-term-icons.jpg)

Each Term has title, slug and other meta-data. So lets say you’ve a term Shop, and its slug is shop, you can set its icon with hooks. If you want to show term icon for your translated Term, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getElegantHomeTermsIconMap()` method. Then look for _iconMap, and edit existing or add new entry for your desired term, add the slug-name of your term eg: 

```dart
Map<String, dynamic> _iconMap = {
    "for-rent": Icons.vpn_key_outlined,
    "residential": Icons.apartment_outlined,

    "shop": Icons.store_outlined,
    "متجر": Icons.store_outlined,     //<-- translated slug of term for shop
    ...
};
```


The Icons.xxxxx are coded from Google Material icons here: https://fonts.google.com/icons
