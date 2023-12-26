---
title: Add Floating Action Button
category: Hooks & Widgets
permalink: hooks-widgets/add_floating_action_button
order: 329
---

By default when you enable [Floating Action Button from HouziBuilder](/houzi-builder/customize_navigation_bar), it always open Quick Add Property.

You can customize the Floating Action Button on the Navigation Bar (tab bar). 

To customize the FAB, do following:

1. You need to [Enable FAB via HouziBuilder](/houzi-builder/customize_navigation_bar), then export and save configurations.
2. Customize it with hooks.

> **Note**: Enabling FAB from Houzi Builder is necessary. For quick enabling, you can add or edit `"show_bottom_navbar_add_button": true,` to your configuration.json file.

To customize FAB, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getAddPlusButtonInBottomBarHook()` method.

You will be provided with some code in this method. Just comment or remove the `return null;` statement and un-comment the commented below code:

Now define your custom *Action*, that you want to perform when the Floating Action Button will be pressed, in the **onPressed** method.

## Code Preview:

```dart
 @override
  AddPlusButtonInBottomBarHook getAddPlusButtonInBottomBarHook() {
    AddPlusButtonInBottomBarHook hook = (BuildContext context) {
      /// If you wish to include a Plus button in the center of the bottom bar,
      /// return your widget else return null.
      ///
      /// Please note that this approach is not compatible with BOTTOM BAR DESIGN_02.

      // return null;

      return Container(
        width: 65,
        height: 65,
        margin: const EdgeInsets.only(top: 0),
        child: FloatingActionButton(
          backgroundColor: AppThemePreferences.appSecondaryColor,
          child: Icon(Icons.add,color: Colors.white,size: 35),
          elevation: 4.0,
          onPressed: () {
            // add your custom action here
          },
        ),
      );
    };

    return hook;
  }
```

> **Note**: Add Floating Action Button is **not availble** for *Navigation Bar Design 02*. 

*Added in version 1.3.8*

