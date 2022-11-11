---
title: Customize Search By Id
category: Hooks & Widgets
order: 16
---


If you want to add item in Settings, go to `Project_HOME  > lib > Hooks.dart`. Look for the `getSearchByIdHook()` method.

```
static getProfileItemHook(){
    SearchByIdWidgetHook searchByIdWidgetHook = (context) {
      Widget searchByIdWidget = null;
      // Widget searchByIdWidget = SearchByIdWidget();

      return searchByIdWidget;
    };
  }
```

### Steps to Customize Search By Id Button Widget: 

1. If you want to hide the **Search By Id Button Widget**, define **null** against `searchByIdWidget`.
2. If you want to show the default **Search By Id Button Widget**, define **SearchByIdWidget()** against `searchByIdWidget`.
3. If you want to show your custom widget, define **yourWidget()** against `searchByIdWidget`.
4. Finally return the widget `searchByIdWidget`.
5. Restart the App.

#### Example code snippets:

```

// Hide Search By Id Button Widget
Widget searchByIdWidget = null;
return searchByIdWidget;

// Default Search By Id Button Widget
Widget searchByIdWidget = SearchByIdWidget();
return searchByIdWidget;

// Custom Widget
 Widget searchByIdWidget = GestureDetector(
  child: Icon(Icons.search_outlined),
  onTap: () {
    // Perform Some Function here
  },
);

return searchByIdWidget;

```