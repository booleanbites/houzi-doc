---
title: Set Marker Title in Map View
category: Hooks & Widgets
order: 17
---

If you want to set Marker Title in Map View, go to `Project_HOME  > lib > Hooks.dart`. Look for the `getMarkerTitleHook()` method.

Set title to the marker in MapView. Instance of Article/Property is provided. You can choose whatever the title you want to set, it can be property title, id, price or anything

```
static getMarkerTitleHook() {
    MarkerTitleHook markerTitleHook = (Article article) {
      /// If you want to set price as a title, use this piece of code
      // String propertyPrice = "";
      // String firstPrice = "";
      // String _finalPrice = "";
      //
      // if (article.propertyDetailsMap!.containsKey(PRICE)) {
      //   propertyPrice = article.propertyDetailsMap![PRICE]!;
      // }
      // if (article.propertyDetailsMap!.containsKey(FIRST_PRICE)) {
      //   firstPrice = article.propertyDetailsMap![FIRST_PRICE]!;
      // }
      //
      // _finalPrice = GenericMethods.priceFormatter(propertyPrice, firstPrice);
      // return _finalPrice;

      String markerTitle = article.title!;
      return markerTitle; // return title here (should be string type) 
    };

    return markerTitleHook;

  }
```

