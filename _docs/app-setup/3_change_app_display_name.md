---
title: App display name
category: App Setup
permalink: app-setup/change_app_display_name
order: 203
---

By default the display name for the app is set to Houzi. For Android, you can change it in AndroidManifest.xml. For iOS, you can change it in info.plist.

## Android

Open AndroidStudio, expand `android > app > src > main` project folder,  and find  AndroidManifest.xml

Look for the application tag, and replace android:label attribute with your own display name.
 

## For iOS

open Xcode, and click on the project name (Runner) on the top left side and click on Info tab, you should see the Bundle Identifier option, change its value with your own. `Project_HOME > ios > Runner > Info > Bundle Name`


Replace Bundle Name value with your display name.