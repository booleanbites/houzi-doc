---
title: Add item in Settings
category: Hooks & Widgets
permalink: hooks-widgets/add_item_settings
order: 303
---


If you want to add item in Settings, go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getSettingsItemHook()` method.

```dart
static getSettingsItemHook(){
    SettingsHook settingsHook = (BuildContext context){
      List<dynamic> settingsItemHookList = [
        // Add menu item map here
      ];
      return settingsItemHookList;
    };
  }
```

There are two types of items that you can add to `Settings`:
1. Single Settings Menu item.
2. Settings Menu Section with Menu items.

### Steps to Add **Single Settings Menu item:**  

1. Copy and paste the sample code of **singleSettingsMenuItem**.
   
   ```dart

   Widget singleSettingsMenuItem = genericWidgetRow(
        iconData: ,
        text: ,
        onTap: (){
          // Some Function()
        },
        removeDecoration: ,
        padding: ,
        sectionType: "preferences",
      );

      Map<String, dynamic> singleSettingsMenuItemMap = {
        "sectionType" : "preferences",
        "menuItem" : singleSettingsMenuItem,
      };

      ```
2. Provide **IconData** against the `iconData` field.
3. Provide **Item Label** against the `text` field.
4. Provide **action** that you want to perform on tap of this item, against the `onTap` field.
5. If you do not want a **divider** under the menu item, set the value of `removeDecoration` to **true**.
6. If you want to manually adjust the padding of menu item, provide **Padding** against the `padding` field.
7. Rename the widget `singleSettingsMenuItem`, as you like.
8. There are two sections on 'Settings' page:
    1. preferences.
    2. community_standards_and_legal_policies.   

    > If you want to place the menu item in specific section, define the section type (**preferences** or **community_standards_and_legal_policies**) against the `sectionType` key in `singleSettingsMenuItemMap`.

9.  Add the widget name (e.g. **singleSettingsMenuItem**, if not changed) against the `menuItem` key in **singleSettingsMenuItemMap**.
10. Rename the widget **singleSettingsMenuItemMap**, as you like.
11. Finally add the Widget Map name to the List `settingsItemHookList`.
12. Restart the App.

#### Example code for **Single Settings Menu item:**

```dart

Widget descriptionSettingsMenuItem = genericWidgetRow(
            iconData: Icons.description_outlined,
            text: "Temporary Show Description",
            onTap: (){
                // Some Function()
                print("Showing Description.........................");
            },
            removeDecoration: true,
            padding: EdgeInsets.symmetric(horizontal: 20.0, vertical: 10.0),
        );

        Map<String, dynamic> descriptionSettingsMenuItemMap = {
            "sectionType" : "",
            "menuItem" : descriptionSettingsMenuItem,
        };

        Widget helpSettingsMenuItem = genericWidgetRow(
            iconData: Icons.help_outlined,
            text: "Temporary Show Help",
            onTap: (){
                // Some Function()
                print("Showing Description.........................");
            },
            removeDecoration: true,
            padding: EdgeInsets.symmetric(horizontal: 20.0, vertical: 10.0),
        );

        Map<String, dynamic> helpSettingsMenuItemMap = {
            "sectionType" : "",
            "menuItem" : helpSettingsMenuItem,
        };


        List<dynamic> settingsItemHookList = [
            descriptionSettingsMenuItemMap,
            helpSettingsMenuItemMap,
        ];

```

### Steps to Add **Settings Menu Section with Menu items:**  

1. Copy and paste the sample code of **settingsMenuSectionWithItems**.
   
   ```dart

   Widget settingsMenuSectionWithItems = genericSettingsWidget(
        headingText: "",
        headingSubTitleText: "",
        removeDecoration: false,
        enableTopDecoration: true,
        enableBottomDecoration: false,
        body: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            // define your menu items here
          ],
        ),
      );

      Map<String, dynamic> settingsMenuSectionWithItemsMap = {
        "sectionType" : "",
        "menuItem" : settingsMenuSectionWithItems,
      };

      ```
2. Provide **Section Heading Name** against the 'headingText' field.
3. Provide  **Section Sub-Heading Name** against the 'headingSubTitleText' field.
4. If you do not want a **divider** under the menu item, set the value of `removeDecoration` to **true**.
5. If you want to provide a **divider** above the menu section, set the value of `enableTopDecoration` to **true**.
6. If you want to provide a **divider** below the menu section, set the value of `enableBottomDecoration` to **true**.
7. Rename the widget `settingsMenuSectionWithItems`, as you like.
8. Add the menu items in the `childern` section of the `body`.
9. Leave the empty value against `sectionType` key in **settingsMenuSectionWithItemsMap**.
10. Add the widget name (e.g. **settingsMenuSectionWithItems**, if not changed) against the `menuItem` key in **settingsMenuSectionWithItemsMap**.
11. Rename the widget **settingsMenuSectionWithItemsMap**, as you like.
12. Finally add the Widget Map name to the List `settingsItemHookList`.
13. Restart the App.

#### Example code for `Settings Menu Section with items:`

```dart
Widget settingsMenuSectionWithItems = genericSettingsWidget(
    headingText: "Temporary Heading",
    headingSubTitleText: "Temporary Sub Heading",
    enableTopDecoration: true,
    enableBottomDecoration: false,
    body: Column(
    crossAxisAlignment: CrossAxisAlignment.start,
    children: [
            genericWidgetRow(
                iconData: Icons.description_outlined,
                text: "Temporary Show Description",
                onTap: (){
                    // Some Function()
                    print("Showing Description.........................");
                    },
                removeDecoration: true,
                ),
                genericWidgetRow(
                iconData: Icons.help_outlined,
                text: "Temporary Help Description",
                onTap: (){
                    // Some Function()
                    print("Showing Help.........................");
                    },
                removeDecoration: true,
            ),
        ],
    ),
);

Map<String, dynamic> settingsMenuSectionWithItemsMap = {
    "sectionType" : "",
    "menuItem" : settingsMenuSectionWithItems,
};


List<dynamic> settingsItemHookList = [
    settingsMenuSectionWithItemsMap,
];

```