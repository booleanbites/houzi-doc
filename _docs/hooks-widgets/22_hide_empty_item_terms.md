---
title: Hide empty items in Terms
category: Hooks & Widgets
permalink: hooks-widgets/hide_empty_terms
order: 322
---

If you want to hide empty cities, areas or states, you can use follwing hook to hide empty enteries in any term.
Terms are added on backend, and there can be lot of terms with empty data
    
If this function returns `true`, for a Term, the empty enteries in that terms will be hidden.

For example, for property_city, you've three cities [New York, Miami, Los Angeles]
One of the city doesn't have any listing. Meaning you don't have any property listing in that
city. So do you want to hide the city from selection that has zero listings? return true
when it asks for term 'property_city'

Specially useful for property_area, as it can be filtered out to show only non-empty areas.

`Project_HOME  > lib > hooks_v2.dart`

Look for the `hideEmptyTerm()` method. Add key value pair in a given map. eg: 
```dart
  HideEmptyTerm shouldHide = (String termName) {
    
    if (termName == 'property_city') {
      return true; //return true to hide empty cities.
    }
    if (termName == 'property_area') {
      return true; //return true to hide empty areas.
    }
    
    return false; //false shows all.
  };
  
```

The terms names are the one Houzez uses on the admin panel. These consist of following terms: property_country, property_state, property_city, property_area, property_type, property_features, property_label, property_status. 

*Added in version 1.2.0*

