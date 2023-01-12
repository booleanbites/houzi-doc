---
title: Set default Language
category: Hooks & Widgets
order: 10
---

If you want to set default langauge, go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getDefaultLanguageHook()` method. 

```
DefaultLanguageCodeHook defaultLanguageCodeHook = () {
      /// Add here your default language code
      return "en";
    };
```

