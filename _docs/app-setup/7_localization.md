---
title: Localization (Translation)
category: App Setup
permalink: app-setup/localization
order: 207
---

## Add new language?
 Follow Hooks and Widget section on how to [Add New Language](/hooks-widgets/add_new_language). 

## Philosophy
There are two types of strings that we need to handle, first one is app level/static strings and the other is for translating dynamic strings sent from the server. Both of them can be handle in one file

We’ve generated an exhaustive English translation file. You can copy this file and rename it with your own language.

For translation, copy and duplicate the following file with your own locale.

Go to the `Project_HOME > assets > localization > en_localization.json` and duplicate and translate the values on the right side in the new file like this:
```json
"search": "Search"
To Dutch like this:
"search": "zoekopdracht"
```

The traditional localisation method handles strings that are already included in the project source, but there are certain events where strings come from the server, and we still need to translate those.

**For example** we cannot know how many property statuses or how many property features  are there on your server, so we also covered a dynamic way of localisation for those strings.

Find json files placed in following folder:

`Project_HOME > assets > localization > en_localization.json`

Add missing / non translated strings to the English file, and then copy this file in the same folder, prefix this to your locale like `ar_localization.json` for Arabic and start adding strings that are coming from your server in a json format.

If you need to use this custom translation at any place, use following method:
```dart
String localized = UtilityMethods.getLocalizedString("String Key in json");
```
