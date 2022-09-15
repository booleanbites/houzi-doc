---
title: Add Header in webservice
category: Hooks & Widgets
order: 9
---

If you want to add Header in webservice, you need to open following file:

`Project_HOME  > lib > Hooks.dart`

Look for the `getHeaderMap()` method. Add key value pair in a given map. eg: 
```
  …
    Map<String, dynamic> map = {
      ...
      "your_key_here": "your_value_here",
      
      //like this
      "secret_key": "!@#%^&*()_-+=",
    };
  …
```

