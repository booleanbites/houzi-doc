---
title: Add item in drawer
category: App Setup
order: 12
---

If you want to add item in drawer, you need to open following file:

`Project_HOME  > lib > Hooks.dart`

Look for the `getDrawerItems()` method. Add the DrawerItem objects into the list. eg: 
```
  …
  static getDrawerItems() {
    DrawerHook drawerHook = (BuildContext context) {
      // make an item of drawer like this
      DrawerItem drawerItem = DrawerItem(
        sectionType: "hook",        // name of the section
        title: "Hook no 1",         // title of the section
        checkLogin: false,          // login is required to see this section
        enable: true,               // hide or show
        insertAt: 5,                // give position where you want to place
        icon: Icons.real_estate_agent, // give icon to your section
        onTap: () {                 // perform some action on tap 
          Navigator.push(
            context,
            MaterialPageRoute(
              builder: (context) => AllAgents(),
            ),
          );
        },     
      );

      List<dynamic> drawerItemList = [drawerItem]; // add the objects in this list

      return drawerItemList;
    };

    return drawerHook;
  }
  …
```

