---
title: Setup a Maps api key for Android and iOS projects
category: Tools
order: 8
---

Once you acquire the key, you need to place it in Android and iOS projects.

### Android
Open AndroidStudio, expand `android > app > src > main > res > values` project folder,  and find  `strings.xml` file in your Android project. And look for the map key `map_api_key` and paste the key in value attributes.

### iOS
Open Xcode and goto `AppDelegate.swift`, look for `GMSServices.provideAPIKey()` and paste your key in there.