---
title: Add Custom Drawer Menu Row Design
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_drawer_menu_row_design
order: 338
---

Houzi proivdes you with the **getDrawerMenuItemDesignHook()**  for providing widget for custom drawer menu row design. Simply open the file from the following path:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getDrawerMenuItemDesignHook()` method.

```dart
@override
  DrawerMenuItemDesignHook? getDrawerMenuItemDesignHook() {
    DrawerMenuItemDesignHook drawerMenuItemDesignHook = ({
      required iconData, required label, required onTap, required selectedItem}) {
      // return your design widget here
      return null;
    };

    // return drawerMenuItemDesignHook;
    return null;
  }
```

You are provided with the following parameter:

- [label](#label)  
- [iconData](#icondata)  
- [selectedItem](#selecteditem)  
- [onTap](#ontap)  

Let's dive into the details of each parameter.

## label

You are provided with the String type **label** parameter which is the label of the row. You can use the this parameter as label text in your custom design widget.

## iconData

You are provided with the IconData type **iconData** parameter which is used in the Icon widget of the row. You can use the this parameter in the Icon widget of your custom design widget.

## selectedItem

You are provided with the String type **selectedItem** parameter which is the current selected item of the drawer menu. You can use the this parameter in your custom design widget accordingly.

## onTap

You are provided with the VoidCallback type **onTap** parameter which is the callback on drawer menu row. You can use the this parameter in your custom design widget accordingly.


>  Return `drawerMenuItemDesignHook` instead of null for the modifications to work. 

```dart
@override
  DrawerMenuItemDesignHook? getDrawerMenuItemDesignHook() {
    DrawerMenuItemDesignHook drawerMenuItemDesignHook = ({
      required iconData, required label, required onTap, required selectedItem}) {
      // return your design widget here
    };

    return drawerMenuItemDesignHook;
  }
```

>  After modifications, restart the app and the changes will reflect in your app.