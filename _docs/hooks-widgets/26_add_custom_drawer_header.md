---
title: Add Custom Header in Drawer
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_drawer_header
order: 326
---

If you want to add a custom drawer header, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getDrawerHeaderHook()` method. You are provided with:
- `context` (BuildContext): The build context of the application.
- `appName` (String): The name of the application.
- `appIconPath` (String): The path to the application icon.
- `userProfileName` (String?): The name of the user's profile. It can be `null`.
- `userProfileImageUrl` (String?): The URL of the user's profile image. It can be `null`.

```dart
@override
DrawerHeaderHook getDrawerHeaderHook() {
  DrawerHeaderHook drawerHeaderHook = (
    BuildContext context,
    String appName,
    String appIconPath,
    String? userProfileName,
    String? userProfileImageUrl,
  ) {
    Widget? drawerHeaderWidget;
    // Customization logic for the drawer header goes here
    return drawerHeaderWidget;
  };
  return drawerHeaderHook;
}
```

Make sure to replace the placeholder comments with your specific customization logic for the drawer header.

*Added in version 1.3.0*

