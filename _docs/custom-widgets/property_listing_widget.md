---
title: Change design of property listing
category: Custom Widgets
order: 7
---

If you want to change property listing, you need to open following file:

`Project_HOME  > lib > Hooks.dart`

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

