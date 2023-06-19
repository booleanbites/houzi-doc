---
title: Change design of Agency listing
category: Hooks & Widgets
permalink: hooks-widgets/agency_item_design_custom
order: 309
---

If you want to change property listing, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getAgencyItemHook()` method. The Agency instance is provided to you, return the widget that you want to show. eg: 
```dart
  …
    AgencyItemHook agencyItemHook = (Agency agency) {
      return Container(
        child: Center(child: Text(agency.title)),
      );
    };
  …
```

