---
title: Set default Country Code for Phone Login
category: Hooks & Widgets
permalink: hooks-widgets/set_default_country_code
order: 307
---

If you want to set default Country Code for Phone Login, go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getDefaultCountryCodeHook()` method.

```
DefaultCountryCodeHook defaultCountryCodeHook = () {
    // return 2 Letter ISO Code to make it default country code for phone login
    return "PK";
};
```

