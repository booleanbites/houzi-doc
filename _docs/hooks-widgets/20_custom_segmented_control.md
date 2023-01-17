---
title: Change Segmented Control Design
category: Hooks & Widgets
permalink: hooks-widgets/segmented_control_design
order: 320
---

If you want to add your own Segmented Control design, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getCustomSegmentedControlHook()` method. The necessary items are provided to you.

1. `dataList` is the list on which segmented control will build.
2. `selectionIndex` is currently selected item index.
3. `onSegmentChosen` is the callback to use when a segmented item is chosen. It is better to use provided `onSegmentChosen` callback as it is handling all the necessary things rather than your own callback.

Return the widget that you want to show. eg: 
```
  …
    CustomSegmentedControlHook customSegmentedControlHook = (context, dataList, selectionIndex, onSegmentChosen) {

      return null; // return null if you want to use default app MaterialSegmentedControl
    };

    return customSegmentedControlHook;
  …
```

