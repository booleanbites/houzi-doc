---
title: Add Custom Widget in Home Sliver App bar
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_widget_in_home_sliver_appbar
order: 324
---

You can show custom widgets to your home pages sliver appbar easily via hooks.

If you want to show a 'custom widget' in Home page sliver appbar, you need to do following things:

- Open file `Project_HOME  > lib > hooks_v2.dart` and look for the `getHomeSliverAppBarBodyHook()` method. 

- You are provided with **_bodyHookMap**, **_bodyWidgetHeight** and **_bodyWidget** parameters. Details of parameters are as follows:

  - Define the height of your widget in the *_bodyWidgetHeight*. 
  - Define the your custom widget in the *_bodyWidget*.
  - Define both of these parameters in the *_bodyHookMap* against the **height** and **widget** keys.

For Example: If you have a custom widget named as **CustomWidget()**, define its height and body and define _bodyHookMap and restart the app.

```dart
  @override
  HomeSliverAppBarBodyHook getHomeSliverAppBarBodyHook() {
    HomeSliverAppBarBodyHook _homeSliverAppBarBodyHook = (context) {
      Map<String, dynamic>? _bodyHookMap;
      double? _bodyWidgetHeight;
      Widget? _bodyWidget;

      // _bodyWidgetHeight = 220;
      // _bodyWidget = CustomWidget();
      
      _bodyHookMap = {
        "height" : _bodyWidgetHeight,
        "widget" : _bodyWidget,
      };
      return _bodyHookMap;
    };
    return _homeSliverAppBarBodyHook;
  }
  
```


*Added in version 1.3.0*

