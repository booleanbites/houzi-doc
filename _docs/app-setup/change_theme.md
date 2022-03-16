---
title: Changing Theme Colors
category: App Setup
order: 2
---

Open the file 
```
houzi > packages > houzi_package > lib > files > app_preferences > app_preferences.dart
```

Go to the ‘Colors’ section.

If you want to change the primary color of the app. Define a custom color code map with RGB value of color with different opacities. After defining the map, define the custom app primary color as MaterialColor with the hex value of color and the defined map. Example below:
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

There’re many colors, styles and different icons defined in this file, you can replace or modify these with your likings.

