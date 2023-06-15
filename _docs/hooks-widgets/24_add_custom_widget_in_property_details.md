---
title: Add Custom Widget in Property Details
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_widget_in_property_details
order: 324
---

If you want to add a 'Custom widget' in Property Details page, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getWidgetHook()` method. You are provided with `hook` and `article` parameters. In the `if_statement()` comparison, replace the `HOOK_NAME` with your specific hook name (which you have already defined in the HouziBuilder Desktop Application.) and replace your Custom widget with `WIDGET`.  

You are provided with the Property Article Information as the object 'article'. You and get your desired information from the 'article' and display in your Custom Widget.

For Example: If you have a custom widget named as 'custom-widget'. Just replace the 'HOOK_NAME' with 'custom-widget' and return your widget as follows:
```dart
  PropertyPageWidgetsHook detailsHook = (
      BuildContext context,
      Article article,
      String hook,
    ) {
      
      /// This is sample code:
      /// if (hook == 'HOOK_NAME') {
      ///   return WIDGET;
      /// }

      if (hook == 'custom-widget') {
          return Conatiner(
            height: 120,
            child: Text("I'm custom widget"),
          );
        }

      return null;
    };
  
```

    
    
    
> **Note**: You can **re-arrange** the position of your `custom widget` & you can **re-name** your `custom widget` from the **HouziBuilder** Desktop App. 

*Added in version 1.3.0*

