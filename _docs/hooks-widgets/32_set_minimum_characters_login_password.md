---
title: Set minimum characters for Login Password
category: Hooks & Widgets
permalink: hooks-widgets/set_minimum_characters_login_password
order: 332
---

If you want to set the minimum character for the password of the Login and User-Sign-up, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getMinimumPasswordLengthHook()` method. By default, the minimum characters limit is set to 8. Replace it according to your requirement.

After modifications, restart the app and the changes will reflect on Maps.

```dart
@override
  MinimumPasswordLengthHook getMinimumPasswordLengthHook() {
    MinimumPasswordLengthHook minimumPasswordLengthHook = () {
      return 8;
    };
    return minimumPasswordLengthHook;
  }
```

*Added in version 1.3.9*

