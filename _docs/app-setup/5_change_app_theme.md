---
title: Changing Theme Colors
category: App Setup
permalink: app-setup/change_app_theme
order: 205
---

## Change Theme Colors by Houzi Config
 You can use Houzi Config Builder to change [Theme Colors](/houzi-config-builder/change-theme) and many other options. 


## Change Theme Colors by config.json
 You can change colors from config by replacing ******* with your own color code. Open the `Project_HOME > assests > configuration > configuration.json` file, and look for the following keys:

**Note**: The `FF`, `4D`, `99` are used for opacity, if you want to change the opacity then modify them otherwise leave it as it is: 

 ```json
 "primary_color": "#FF******",
  "secondary_color": "#FF******",
  "icon_tint_color": "#FF******",
  "bottom_tab_bar_tint_color": "#FF******",
  "slider_tint_color": "#FF******",
  "selected_item_background_color": "#4D******",
  "un_selected_item_background_color": "#1A808080",
  "selected_item_text_color": "#FF******",
  "un_selected_item_text_color": "#8A000000",
  "action_button_background_color": "#FF******",
  "featured_label_background_color": "#99******",
 ```


<!-- ## Change Theme Colors by AppPreferences
Open the file 
```
houzi > packages > houzi_package > lib > files > app_preferences > app_preferences.dart
```

Go to the ‘Colors’ section.

If you want to change the primary color of the app. Define a custom color code map with RGB value of color with different opacities. After defining the map, define the custom app primary color as `MaterialColor` with the hex value of color and the defined map. Example below:
```
/// Define your custom color swatches.
Map<int, Color> primaryColorCodes = {
 50: Color.fromRGBO(37, 173, 222, .1),
 100: Color.fromRGBO(37, 173, 222, .2),
 200: Color.fromRGBO(37, 173, 222, .3),
 300: Color.fromRGBO(37, 173, 222, .4),
 400: Color.fromRGBO(37, 173, 222, .5),
 500: Color.fromRGBO(37, 173, 222, .6),
 600: Color.fromRGBO(37, 173, 222, .7),
 700: Color.fromRGBO(37, 173, 222, .8),
 800: Color.fromRGBO(37, 173, 222, .9),
 900: Color.fromRGBO(37, 173, 222, 1),
};
MaterialColor primaryColor = MaterialColor(0xFF25ADDE, primaryColorCodes);
```

Change the `appPrimaryColor` with this custom defined material color primaryColor.

There’re many colors, styles and different icons defined in this file, you can replace or modify these with your likings. -->

