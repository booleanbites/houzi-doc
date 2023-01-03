---
title: Add item in Profile tab
category: Hooks & Widgets
order: 15
---


If you want to add item in profile tab, go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getProfileItemHook()` method.

```
static getProfileItemHook(){
    ProfileHook profileHook = (BuildContext context){
      List<Widget> profileItemHookList = [
        // Add menu item map here
      ];
      return profileItemHookList;
    };
  }
```

### Steps to Add Menu item: 

1. Copy and paste the sample code of **menuItem**.
   
   ```

   Widget menuItem = genericWidgetRow(
        iconData: ,
        text: ,
        onTap: (){
          // Some Function()
        },
        removeDecoration: ,
        padding: ,
      );

      ```
2. Provide **IconData** against the `iconData` field.
3. Provide **Item Label** against the `text` field.
4. Provide **action** that you want to perform on tap of this item, against the `onTap` field.
5. If you do not want a **divider** under the menu item, set the value of `removeDecoration` to **true**.
6. If you want to manually adjust the padding of menu item, provide **Padding** against the `padding` field.
7. Rename the widget `menuItem`, as you like.
8. Finally add the Widget to the List `profileItemHookList`.
9. Restart the App.

#### Example code for Menu item:

```

Widget descriptionMenuItem = genericWidgetRow(
  iconData: Icons.description_outlined,
  text: "Temporary Show Description",
  onTap: (){
    // Some Function()
    print("Showing Description.........................");
  },
  // removeDecoration: true,
  // padding: EdgeInsets.symmetric(horizontal: 20.0, vertical: 10.0),
);

Widget helpMenuItem = genericWidgetRow(
  iconData: Icons.help_outlined,
  text: "Temporary Show Help",
  onTap: (){
    // Some Function()
    print("Showing Description.........................");
  },
  // removeDecoration: true,
  // padding: EdgeInsets.symmetric(horizontal: 20.0, vertical: 10.0),
);

List<Widget> profileItemHookList = [
  // Add menu item map here
  descriptionMenuItem,
  helpMenuItem,
];

```