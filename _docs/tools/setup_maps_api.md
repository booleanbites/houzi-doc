---
title: Setup a Maps api key for Android and iOS projects
category: Tools Setup
order: 8
---

Once you have setup the project on [Google Cloud](https://developers.google.com/maps/documentation/android-sdk/start#get-key), you need to acquire the key, and place it in Android and iOS projects.

## Android
Open AndroidStudio, expand `android > app > src > main > res > values` project folder,  and find  `strings.xml` file in your Android project. And look for the map key `map_api_key` and paste the key in value attributes.

## iOS
Open Xcode and goto `AppDelegate.swift`, look for `GMSServices.provideAPIKey()` and paste your key in there.