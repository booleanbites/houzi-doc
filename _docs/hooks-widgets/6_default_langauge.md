---
title: Set default Language
category: Hooks & Widgets
permalink: hooks-widgets/set_default_language
order: 306
---

If you want to set default langauge, go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getDefaultLanguageHook()` method. 

```dart
DefaultLanguageCodeHook defaultLanguageCodeHook = () {
      /// Add here your default language code
      return "en";
    };
```

