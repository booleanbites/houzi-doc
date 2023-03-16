---
title: Hide Show Price
category: Hooks & Widgets
permalink: hooks-widgets/hide_show_price
order: 319
---

If you want to hide price on property cards or in property details page, you can use following hook. 

Go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getHidePriceHook()` method. For e.g:

```
@override
HidePriceHook getHidePriceHook() {
  HidePriceHook hidePriceHook = () {

    bool hidePropertyPrice = false;

    return hidePropertyPrice;
  };

  return hidePriceHook;
}
```

You can return conditional checks as well, like if you want to hide price by default and show to logged in users only. Or if you want to show price to certain user roles, example below:

```
// Use isLoggedIn, if you want to show price to logged in users.
bool isLoggedIn = HiveStorageManager.isUserLoggedIn();
hidePropertyPrice = isLoggedIn ? false : true;

// Use roles, if you want to show price to certain roles for logged in user.
String userRole = HiveStorageManager.getUserRole() ?? "";
hidePropertyPrice = (userRole == ROLE_ADMINISTRATOR || userRole == USER_ROLE_HOUZEZ_AGENCY_VALUE) ? false : true;
```

This will hide listing price on property cards as well as on property details pages.

*Added in version 1.2.0*