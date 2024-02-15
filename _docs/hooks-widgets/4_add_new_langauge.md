---
title: Add new Language
category: Hooks & Widgets
permalink: hooks-widgets/add_new_language
order: 304
---

If you want to add new langauge, you have to follow some few steps:

#### Step 1
First open `Project_HOME  > assets > localization`, simply make a copy of English localization and rename it as YOUR-LANGUAGE-CODE_localization.json then translate the right side of sentences in your language. 

> *Note: Your file name must contain language code like YOUR-LANGUAGE-CODE_localization.json (e.g. en_localization.json).

> *If you want to use different **script** for the same language like Chinese zh-Hant and zh-Hans, rename your file including the script code. For example, zh_Hant_localization.json etc.


#### Step 2
You need to add the new files path in `pubspec.yaml`, so it can be bundled in final app binary after compile. Open file `Project_HOME > pubspec.yaml` and find the assets section. Copy your localized strings file name and mention it like following example.

```yaml
assets:
  ...
    # if you are not using different script:
    - assets/localization/YOUR-LANGUAGE-CODE_localization.json
    - assets/localization/en_localization.json

    # if you are using different script, add script code as well:
    - assets/localization/YOUR-LANGUAGE-CODE_SCRIPT-CODE_localization.json
    - assets/localization/zh-Hant_localization.json
  ...
```


#### Step 3
Now go to `Project_HOME  > lib > hooks_v2.dart` and look for the `getLanguageCodeAndName()` method. Specify your language code and language name.

**[Optional]** You can also specify *scriptCode*, *countryCode* and *languageFileName*.

```dart
  …
  static getLanguageCodeAndName() {
    LanguageHook languageHook = () {

      Map<String,dynamic> russianLanguageMap = {
        "languageName": "Russian",          
        "languageCode": "ru"                
      };

       Map<String,String> chineseLanguageMap = {
        "languageName": "Chinese (Traditional)",
        "languageCode": "zh",
        "scriptCode": "Hant",
        "countryCode": "CN",
        "languageFileName": "zh_Hant_localization.json",
      };

      Map<String,dynamic> yourLanguageMap = {
        "languageName": "YOUR-LANGUAGE-NAME",      // Specify your language name
        "languageCode": "YOUR-LANGUAGE-CODE"       // Specify your language code
        "scriptCode": "YOUR-SCRIPT-CODE"       // [Optional] Specify your script code
        "countryCode": "YOUR-COUNTRY-CODE"       // [Optional] Specify your country code
        "languageFileName": "YOUR-LANGUAGE-FILE-NAME"       // [Optional] Specify your language file name
      };

      List<dynamic> languageList = [russianLanguageMap, chineseLanguageMap, yourLanguageMap];  //add your map here
      return languageList;
    };

    return languageHook;
  }
  …
```
> *Note: You can add yourLanguageMap in the languageList without the Optional fields. In simple words, the optional fields can be removed.

