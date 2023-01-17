---
title: Change design of Agency listing
category: Hooks & Widgets
permalink: agency_item_design_custom
order: 9
---

If you want to change property listing, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getAgencyItemHook()` method. The Agency instance is provided to you, return the widget that you want to show. eg: 
```
  …
    AgencyItemHook agencyItemHook = (Agency agency) {
      return Container(
        child: Center(child: Text(agency.title)),
      );
    };
  …
```

