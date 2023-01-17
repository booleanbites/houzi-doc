---
title: Change design of Term
category: Hooks & Widgets
permalink: hooks-widgets/term_widget_item_design_custom
order: 312
---

If you want to change Term Widget design, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getTermItemHook()` method. The metaDataList list is provided to you, return the widget that you want to show. eg: 
```
  …
    TermItemHook termItemHook = (List metaDataList) {

      return //your widget here;
    };
  …
```

