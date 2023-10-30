---
title: Add Custom Widget in Navigation Bar
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_widget_in_navigation_bar
order: 328
---

If you want to add a custom widget in Navigation Bar, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getNavbarWidgetsHook()` method. You are provided with `hookName` parameter. In the `if_statement()` comparison, replace the `HOOK_NAME` with your specific hookName (which you have already defined in the HouziBuilder Desktop Application.) and replace your Custom widget with `WIDGET`. 

For Example: If you have a custom widget named as `custom-widget`. Just replace the `HOOK_NAME` with `custom-widget` and return your widget as follows:

## Code Preview:

```dart
  @override
  NavbarWidgetsHook getNavbarWidgetsHook() {
    NavbarWidgetsHook navbarWidgetsHook = (
        BuildContext context,
        String? hookName,
        ) {

      //      This is sample code:
      //      if (hookName == 'HOOK_NAME') {
      //        return WIDGET;
      //      }

      if (hookName == 'custom-widget') {
        return Container(
          height: 100,
          child: Text("I'm custom widget"),
        );
      }

      return null;
    };

    return navbarWidgetsHook;
  }
```

> **Note**: You can **re-arrange** the position of your **custom widget** and you can **re-name** your **custom widget** from the **Houzi Builder** Desktop App. 

*Added in version 1.3.8*

