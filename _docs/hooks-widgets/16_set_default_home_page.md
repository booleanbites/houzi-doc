---
title: Set default HomePage
category: Hooks & Widgets
permalink: hooks-widgets/default_home_page
order: 316
---

If you want to set default HomePage, go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getDefaultHomePageHook()` method. You can choose your default home for the app. You have four options, choose one of the following:
1. home_0   (Home Carousel)
2. home_1   (Home Elegant)
3. home_2   (Home Location)
4. home_3   (Home Tabbed)

```dart
DefaultHomePageHook defaultHomePageHook = () {
  
  return "home_1";

};
```

Otherwise you can set this from Houzi Builder.

