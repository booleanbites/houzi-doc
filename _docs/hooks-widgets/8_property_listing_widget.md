---
title: Change design of Property listing
category: Hooks & Widgets
permalink: property_item_design_custom
order: 8
---

If you want to change property listing, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getPropertyItemHook()` method. The Property/Article instance is provided to you, return the widget that you want to show. eg: 
```
  …
    PropertyItemHook propertyItemHook = (BuildContext context, Article article) {

      return Container(
        child: Center(child: Text(article.title)),
      );

    };
  …
```

