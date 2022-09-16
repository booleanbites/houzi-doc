---
title: Add new Language
category: Hooks & Widgets
order: 9
---

If you want to add new langauge, you have to follow some few steps:

#### Step 1
First open `Project_HOME  > assets > localization`, add your localized strings file here. Your file name must be contain language code like YOUR-LANGUAGE-CODE_localization.json (e.g en_localization.json)


#### Step 2
Then you also have to mention the path in `pubspec.yaml`. Go to `Project_HOME > pubspec.yaml` and find the assets section. Copy your localized strings file name and mention it.
```
assets:
  ...

    - assets/localization/en_localization.json
    - assets/localization/YOUR-LANGUAGE-CODE_localization.json

  ...
```


#### Step 3
Now go to `Project_HOME  > lib > Hooks.dart` and look for the `getLanguageCodeAndName()` method. Specify your language code and language name here e.g: 

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


