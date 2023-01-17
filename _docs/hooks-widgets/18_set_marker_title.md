---
title: Set Marker Title in Map View
category: Hooks & Widgets
permalink: hooks_widgets/map_marker_title
order: 18
---

You can set Marker Title in Map View, go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getMarkerTitleHook()` method.

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

