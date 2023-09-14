---
title: Add Custom Widget in Drawer
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_widget_in_drawer
order: 326
---

If you want to add a custom widget in drawer, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getDrawerWidgetsHook()` method. You are provided with `hookName` parameter. In the `if_statement()` comparison, replace the `HOOK_NAME` with your specific hookName (which you have already defined in the HouziBuilder Desktop Application.) and replace your Custom widget with `WIDGET`. 

For Example: If you have a custom widget named as `custom-widget`. Just replace the `HOOK_NAME` with `custom-widget` and return your widget as follows:

```dart
@override
  DrawerWidgetsHook getDrawerWidgetsHook() {
    DrawerWidgetsHook drawerWidgetsHook = (
        BuildContext context,
        String? hookName) {

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

      
    };

    return drawerWidgetsHook;
  }
```

> **Note**: You can **re-arrange** the position of your `custom widget` & you can **re-name** your `custom widget` from the **HouziBuilder** Desktop App. 

*Added in version 1.3.5*

