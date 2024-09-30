---
title: Setup Maps API key
category: Tools Setup
permalink: tools/setup_maps_api
order: 9
---

<br/>
<iframe width="560" height="315" src="https://www.youtube.com/embed/zTwFI-cPgtk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br/>
<br/>

Once you have setup the project on [Google Cloud](https://developers.google.com/maps/documentation/android-sdk/start#get-key), you need to acquire the [Key](https://developers.google.com/maps/documentation/android-sdk/get-api-key), and place it in Android and iOS projects.

You've to put the API key in configuration.json (automatically or manually) as well as in native project files. This API key is used for Maps, Places search and Static Maps.

### Setup maps api key by Houzi Config
 You can use Houzi Config Builder to save the Maps api key: [Theme Api & Config](/houzi-builder/api_config_setup). 

### Setup maps api key by config.json
 You can change colors from config by replacing ******* with your own color code. Open the `Project_HOME > assests > configuration > configuration.json` file, and look for the following keys:

 ```
  "google_map_api_key": "your_key_here",
 ```

### Additional steps (mandatory)
After adding maps key in configuration.json, its mandatory to add this in native projects as well. Because both platform use native maps sdk to show maps in flutter apps.

#### Android
Open AndroidStudio, expand `android > app > src > main > res > values` project folder,  and find  `strings.xml` file in your Android project. And look for the map key `map_api_key` and paste the key in value attributes.

#### iOS
Open Xcode and goto `AppDelegate.swift`, look for `GMSServices.provideAPIKey()` and paste your key in there.