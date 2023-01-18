---
title: Setup a Maps api key for Android and iOS projects
category: Tools Setup
permalink: tools/setup_maps_api
order: 9
---

Once you have setup the project on [Google Cloud](https://developers.google.com/maps/documentation/android-sdk/start#get-key), you need to acquire the [Key](https://developers.google.com/maps/documentation/android-sdk/get-api-key), and place it in Android and iOS projects.

## Setup maps api key by Houzi Config
 You can use Houzi Config Builder to save the Maps api key: [Theme Api & Config](/houzi-config-builder/api-and-configurations-setup). 

## Setup maps api key by config.json
 You can change colors from config by replacing ******* with your own color code. Open the `Project_HOME > assests > configuration > configuration.json` file, and look for the following keys:

 ```
  "google_map_api_key": "your_key_here",
 ```

## Additional stpes (mandatory)
### Android
Open AndroidStudio, expand `android > app > src > main > res > values` project folder,  and find  `strings.xml` file in your Android project. And look for the map key `map_api_key` and paste the key in value attributes.

### iOS
Open Xcode and goto `AppDelegate.swift`, look for `GMSServices.provideAPIKey()` and paste your key in there.