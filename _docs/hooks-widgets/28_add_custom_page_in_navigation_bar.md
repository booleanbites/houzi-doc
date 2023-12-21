---
title: Add Custom Page in Navigation Bar
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_page_in_navigation_bar
order: 328
---

If you want to add a custom page to Bottom Navigation Bar (Tab bar), you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getNavbarWidgetsHook()` method. You are provided with `hookName` parameter. In the `if_statement()` comparison, replace the `HOOK_NAME` with your specific hookName (which you have already defined in the HouziBuilder Desktop Application.) and replace your Custom widget with `WIDGET`. 

For Example: If you have added a place_holder type widget to navigation bar and name it `custom-widget`. Just replace the `HOOK_NAME` with `custom-widget` and return your widget/page as follows:

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

You can return full page from here. For example, to show :
```dart
  if (hookName == 'custom-widget') {
    return AddPropertyRequest();
  }
```



> **Note**: You can **re-arrange** the position of your **custom widget** and you can **re-name** your **custom widget** from the **Houzi Builder** Desktop App. 

*Added in version 1.3.8*

