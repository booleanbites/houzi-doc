---
title: Set default HomePage
category: Hooks & Widgets
order: 12
---

If you want to set default HomePage, go to `Project_HOME  > lib > Hooks.dart`. Look for the `getDefaultHomePageHook()` method. You can choose your default home for the app. You have four options, choose one of the following:
1. home_0   (Home Carousel)
2. home_1   (Home Elegant)
3. home_2   (Home Location)
4. home_3   (Home Tabbed)

```
DefaultHomePageHook defaultHomePageHook = () {
  
  return "home_1";

};
```

