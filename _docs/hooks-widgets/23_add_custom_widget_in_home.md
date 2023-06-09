---
title: Add Custom Widget in Home
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_widget_in_home
order: 323
---

If you want to add a 'custom widget' in Home page, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getHomeWidgetsHook()` method. You are provided with `hookName` and `isRefreshed` parameters. In the `if_statement()` comparison, replace the `HOOK_NAME` with your specific hookName (which you have already defined in the HouziBuilder Desktop Application.) and return you custom Widget instead of returning `null`.  
For Example: If you have a custom widget named as 'custom-widget'. Just replace the 'HOOK_NAME' with 'custom-widget' and return your widget as follows:
```
  HomeWidgetsHook homeWidgetsHook = (
        BuildContext context,
        String? hookName,
        bool isRefreshed) {

//      This is sample code:
//      if (hookName == 'HOOK_NAME') {
//        return null;
//      }

        if (hookName == 'custom-widget') {
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

