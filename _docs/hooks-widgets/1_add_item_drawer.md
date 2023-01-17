---
title: Add item in drawer
category: Hooks & Widgets
permalink: hooks-widgets/add_item_in_drawer
order: 1
---

If you want to add item in drawer, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getDrawerItems()` method. Add the DrawerItem objects into the list. eg: 
```
  …
  static getDrawerItems() {
    DrawerHook drawerHook = (BuildContext context) {
      // make an item of drawer like this
      DrawerItem drawerItem = DrawerItem(
        sectionType: "section_name",    // name of the section
        title: "Your title here",       // title of the section
        checkLogin: false,              // login is required to see this section
        enable: true,                   // hide or show
        insertAt: 5,                    // give position where you want to place
        icon: Icons.real_estate_agent   // give icon to your section
        onTap: () {                     // perform some action on tap 
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
The Icons.xxxxx are coded from Google Material icons here: https://fonts.google.com/icons

