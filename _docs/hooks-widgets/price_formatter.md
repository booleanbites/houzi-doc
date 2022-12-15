---
title: Set Price Format
category: Hooks & Widgets
order: 19
---

You can set your own price format method in app. There are two price formatter using in Houzi. 

1. 
Marker Title in Map View, go to `Project_HOME  > lib > Hooks.dart`. Look for the `getMarkerTitleHook()` method.

Set title to the marker in MapView. Instance of Article/Property is provided. You can choose whatever the title you want to set, it can be property title, id, price or anything

```
static getMarkerTitleHook() {
    MarkerTitleHook markerTitleHook = (Article article) {
  
      String markerTitle = article.title!;
      return markerTitle; // return title here (should be string type) 
    };

    return markerTitleHook;

  }
```

