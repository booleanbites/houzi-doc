---
title: Add item in drawer
category: Hooks & Widgets
permalink: hooks-widgets/add_item_in_drawer
order: 301
---

To add an item to the drawer, follow these steps:

1. Open the file `hooks_v2.dart` located in the following path within your project: `Project_HOME > lib > hooks_v2.dart`.

2. Locate the `getDrawerItems()` method in the file.

3. Inside the `getDrawerItems()` method, you can add a new item to the drawer by creating a `DrawerItem` object.

4. Specify the properties of the `DrawerItem` object as follows:

- `sectionType`: Provide a unique name for the section. 
- `title`: Set the title of the section.
- `checkLogin`: Specify whether login is required to see this section. Set it to `true` or `false`.
- `enable`: Set whether the section should be hidden or shown. Use `true` or `false`.
- `insertAt`: Specify the position where you want to place the item in the drawer.
- `icon`: Select an appropriate icon for the section from the [Google Material icons library](https://fonts.google.com/icons).
- `onTap`: Define the action to be performed when the item is tapped. You can navigate to a new screen or execute any other desired action.

5. Once you have created the `DrawerItem` object, add it to the `drawerItemList` list.

6. Finally, return the `drawerItemList` from the `getDrawerItems()` method.

To add an expandable item to the drawer, you can follow a similar process with an additional step:

1. Create a new `DrawerItem` object for the expandable item.

2. Set the `expansionTileChildren` property of the expandable item to a list of `DrawerItem` objects. These objects represent the items that will be displayed when the expandable item is clicked.

3. Add the expandable item, along with its child items, to the `drawerItemList` list.

Here's an updated example of the code:

```
@override
DrawerHook getDrawerItems() {
  DrawerHook drawerHook = (BuildContext context) {
    // Add a regular drawer item
    DrawerItem drawerItem = DrawerItem(
      sectionType: "section_name",
      title: "Your title here",
      checkLogin: false,
      enable: true,
      insertAt: 5,
      icon: Icons.real_estate_agent,
      onTap: () {
        Navigator.push(
          context,
          MaterialPageRoute(
            builder: (context) => AllAgents(),
          ),
        );
      },
    );

    // Add an expandable item with child items
    DrawerItem crmExpandedDrawerItem = DrawerItem(
      sectionType: "section_name",
      title: "Your title here",
      checkLogin: false,
      enable: true,
      insertAt: 5,
      icon: Icons.real_estate_agent,
      expansionTileChildren: [
        DrawerItem(
          sectionType: "hook",
          title: "Activities",
          checkLogin: true,
          enable: true,
          icon: Icons.article_outlined,
          onTap: () {
            // Add your code here for desired action
          },
        ),
        DrawerItem(
          sectionType: "hook",
          title: "Inquiries",
          checkLogin: true,
          enable: true,
          icon: Icons.question_answer,
          onTap: () {
            // Add your code here for desired action
          },
        ),
      ],
    );

    List<dynamic> drawerItemList = [drawerItem, crmExpandedDrawerItem];

    return drawerItemList;
  };

  return drawerHook;
}

```

Remember to replace the placeholder values with your desired names, titles, and actions.

Note: The `Icons.xxxxx` values in the code are based on the icons provided by the Google Material icons library. You can find the complete list of available icons [here](https://fonts.google.com/icons). Choose the appropriate icon by selecting the corresponding icon name from the library.

