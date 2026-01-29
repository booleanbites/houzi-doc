---
title: Custom Search Web Params
category: Hooks & Widgets
permalink: hooks-widgets/custom_search_web_params
order: 344
---

Houzi allows you to use **custom query parameters** into search API requests using the **`getCustomSearchWebParamsHook()`**.

This hook is useful if you have customized your backend to filter properties based on additional parameters that are not part of the default Houzi search.

## How to Use

Open `hooks_v2.dart` and locate the **`getCustomSearchWebParamsHook()`** method.

1. Define a `Map<String, dynamic>` with your custom parameter keys and values.
2. Return this map from the function.

```dart
@override
CustomSearchWebParamsHook getCustomSearchWebParamsHook() {
  /* If you have custom params for searching then use the following hook to add
    your params */
  CustomSearchWebParamsHook customSearchWebParamsHook = () {
    /// Use this hook to inject custom query parameters into your search API requests.
    ///
    /// This is useful if you have customized your backend to filter properties
    /// based on additional parameters that are not part of the default Houzi search.
    ///
    /// To use this:
    /// 1. Define a Map<String, dynamic> with your custom parameter keys and values.
    /// 2. Return this map from the function.
    ///
    /// Example is below map having key and its value
    Map<String, dynamic>? customWebServiceParams = {
      /// For Example: You have this key and value as an example
      /// "agent_contact":"+923001234567"
    };

    /// return customWebServiceParams;
    /// Leave it null incase you don't have any custom params
    return null;
  };
  return customSearchWebParamsHook;
}
```

> **Note:** Return `null` if you do not want to pass any custom search parameters.

> After modifications, hot reload or restart the application to see the changes.