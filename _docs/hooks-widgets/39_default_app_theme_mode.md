---
title: Default App Theme Mode
category: Hooks & Widgets
permalink: hooks-widgets/default_app_theme_mode
order: 339 
---

Houzi proivdes you with the **getDefaultAppThemeModeHook()**  for configuring the default app theme mode. You have following theme mode options:

1. light (For the Light Theme Mode).
2. dark (For the Dark Theme Mode).
3. system (For the System Default Theme Mode).

Simply open the file from the following path:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getDefaultAppThemeModeHook()` method. Return the desired option from one of the above mentioned options.

```dart
@override
  DefaultAppThemeModeHook? getDefaultAppThemeModeHook() {
    DefaultAppThemeModeHook defaultAppThemeModeHook = () {
      return "light";
    };

    return defaultAppThemeModeHook;
  }
```


>  After modifications, restart the app and the changes will reflect in your app.