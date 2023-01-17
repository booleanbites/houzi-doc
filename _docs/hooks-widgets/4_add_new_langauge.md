---
title: Add new Language
category: Hooks & Widgets
permalink: add_new_language
order: 4
---

If you want to add new langauge, you have to follow some few steps:

#### Step 1
First open `Project_HOME  > assets > localization`, simply make a copy of English localization and rename it as YOUR-LANGUAGE-CODE_localization.json then translate the right side of sentences in your language. IMPORTANT Your file name must be contain language code like YOUR-LANGUAGE-CODE_localization.json (e.g en_localization.json)


#### Step 2
You need to add the new files path in `pubspec.yaml`, so it can be bundled in final app binary after compile. Open file `Project_HOME > pubspec.yaml` and find the assets section. Copy your localized strings file name and mention it like following example.
```
assets:
  ...
    - assets/localization/en_localization.json
    - assets/localization/YOUR-LANGUAGE-CODE_localization.json
  ...
```


#### Step 3
Now go to `Project_HOME  > lib > hooks_v2.dart` and look for the `getLanguageCodeAndName()` method. Specify your language code and language name here e.g: 

```
  …
  static getLanguageCodeAndName() {
    LanguageHook languageHook = () {

      Map<String,dynamic> russianLanguageMap = {
        "languageName": "Russian",          
        "languageCode": "ru"                
      };

      Map<String,dynamic> yourLanguageMap = {
        "languageName": "YOUR-LANGUAGE-NAME",      // Specify your language name
        "languageCode": "YOUR-LANGUAGE-CODE"       // Specify your language code
      };

      List<dynamic> languageList = [russianLanguageMap, yourLanguageMap];  //add your map here
      return languageList;
    };

    return languageHook;
  }
  …
```


