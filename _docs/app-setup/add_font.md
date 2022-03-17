---
title: Add new font
category: App Setup
order: 6
---

You can add new fonts to the app by copying the font with different weight in the following folder 

`Project_HOME > fonts > new_font_folder`

They should contain font weight files like this:


`Project_HOME > fonts > new_font_folder`
```
> new_font-regular.ttf
> new_font-light.ttf
> new_font-bold.ttf
```

Don’t forget to add new font entry to following file in `pubspec.yaml` fonts section, open file here:
`Project_HOME > pubspec.yaml`

And add the entry in fonts section like this
```
Fonts:
- family: FontNameYouDesire
  Fonts:
    - asset: fonts/new_font_folder/new_font-regular.ttf
    - asset: fonts/new_font_folder/new_font-light.ttf        
    - asset: fonts/new_font_folder/new_font-bold.ttf
```
#### Register font at app level
If you want to apply the font at application level, open following file:
`Project_HOME > packages > houzi_package > lib > main.dart`
Look for the `build()` method and find the darkTheme and theme for MaterialApp object. And change the fontFamily: attribute as follow:
```
//you can also add a condition to change font for multiple locales as well:
darkTheme: ThemeData(
    …
    fontFamily: "FontNameYouWroteInPubSpec",
),
theme: ThemeData(
    …
    fontFamily: "FontNameYouWroteInPubSpec",
)

//You can also use this font in a TextStyle like this
TextStyle(
    …
    fontFamily: "FontNameYouWroteInPubSpec",
); 
```
Read more about fonts here:  https://docs.flutter.dev/cookbook/design/fonts
