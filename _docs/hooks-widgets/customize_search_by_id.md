---
title: Customize Home Right Bar Button Id Widget
category: Hooks & Widgets
order: 16
---


If you want to add item in Settings, go to `Project_HOME  > lib > Hooks.dart`. Look for the `getHomeRightBarButtonWidgetHook()` method.

```
static getHomeRightBarButtonWidgetHook() {
    HomeRightBarButtonWidgetHook homeRightBarButtonWidgetHook = (context) {

      Widget? rightBarButtonHook;
      // Widget rightBarButtonHook = DefaultRightBarButtonIdWidget();

      return rightBarButtonHook;
    };
  }
```

### Steps to Customize Home Right Bar Button Id Widget: 

1. If you want to hide the **Home Right Bar Button Id Widget**, define **null** against `rightBarButtonHook`.
2. If you want to show the default **Home Right Bar Button Id Widget**, define **DefaultRightBarButtonIdWidget()** against `rightBarButtonHook`.
3. If you want to show your custom widget, define **yourWidget()** against `rightBarButtonHook`.
4. Finally return the widget `rightBarButtonHook`.
5. Restart the App.

#### Example code snippets:

```

// Hide Home Right Bar Button Id Widget
Widget rightBarButtonHook = null;
return rightBarButtonHook;

// Default Home Right Bar Button Id Widget
Widget rightBarButtonHook = DefaultRightBarButtonIdWidget();
return rightBarButtonHook;

// Custom Widget
 Widget rightBarButtonHook = GestureDetector(
  child: Icon(Icons.search_outlined),
  onTap: () {
    // Perform Some Function here
  },
);

return rightBarButtonHook;

```