---
title: Migration Guide
category: Tools Setup
permalink: tools/upgrading_future_version
order: 20
---

Always make a backup before updating to the next version.


## Migration Guide for 1.4.7

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

> If you are upgrading from an older version than 1.4.7, you must follow _Migration Guide 1.4.5_ to update your project for Android 15+ (API 36) and 16KB page size support.

Let's assume you simply want to update your houzi_package, updating to 1.4.7 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.7 and replace houzi_package in your existing project. 
- Download and update to Flutter 3.38.xx. [Flutter Download](../tools/flutter_setup).
- Copy `Project_HOME/android/app/src/main/res/drawable/download_icon.xml` to your project in the same location.
- Open AppDelegate.swift at `Project_HOME/ios/Runner/AppDelegate.swift` and find
        `let controller = window.rootViewController as! FlutterViewController`
        replace with
        `let controller = window?.rootViewController as! FlutterViewController` //Notice the ? after window
- Do a project clean. Remove pubspec.lock, ios/Podfile.lock.
- For iOS, you might also need to run `pod install --repo-update` from terminal to referesh the local pod repo. Important: Run this only after you have run the `flutter pub get` in your project root via terminal or from UI.
- **Update Configuration**: You can easily export the latest configuration using the Houzi Builder.
  - Download for Windows: [Houzi Builder](https://github.com/booleanbites/houzi-builder-release/releases/download/1.4.7/HouziBuilder-windows-1.4.7.zip)
  - Download for macOS: [Houzi Builder](https://github.com/booleanbites/houzi-builder-release/releases/download/1.4.7/HouziBuilder-mac-1.4.7.zip)
  
  Once downloaded, use the builder to export the updated configuration.
  
  Alternatively, you can manually update your `configuration.json` with the following:
  ```json
  "home_layout_config": {
       "section_type": "app_bar",
       "layout_tabs": [
            {
                 "term": "all",
                 "sub_term": "all"
            },
            {
                 "term": "property_status",
                 "sub_term": "For Rent",
                 "title": "For Rent",
                 "icon_data": "{\"name\":\"adb_outlined\",\"fontFamily\":\"MaterialIcons\",\"codePoint\":60984}",
                 "search_route_map": {
                      "property_type": [
                           "For Rent"
                      ],
                      "property_type_slug": [
                           "For Rent"
                      ]
                 }
            },
            {
                 "term": "property_status",
                 "sub_term": "For Sale",
                 "title": "For Sale",
                 "icon_data": "{\"name\":\"adb_outlined\",\"fontFamily\":\"MaterialIcons\",\"codePoint\":60984}",
                 "search_route_map": {
                      "property_type": [
                           "For Sale"
                      ],
                      "property_type_slug": [
                           "For Sale"
                      ]
                 }
            }
       ]
  },
  "show_floating_map_widget": false,
  ```
- Rest of configurations like ios project folders should remain same.
- Run and Launch your app on device.

On the wordpress admin panel:
- Remove existing plugin, and upload and activate your Houzi Rest Api version 1.4.7 plugin. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip)
 

## Migration Guide for 1.4.6

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

Let's assume you simply want to update your houzi_package, updating to 1.4.6 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.6 and replace houzi_package in your existing project. 
- Download and update to Flutter 3.35.xx. [Flutter Download](../tools/flutter_setup).
- If you are upgrading from an older version to 1.4.6, you must follow _Migration Guide 1.4.5_ to update your project for Android 15+ (API 36) and 16KB page size support.
- Migrate iOS Project to minimum iOS 15 and make following changes:
  - Open `Project_HOME/ios/Podfile`, update:
    - `platform :ios, '15.0` at line number 2.
  - Open `Project_HOME/ios/Runner/HomeNativeAdViewFactory.swift`, find and replace:
    - find `GADNativeAdView` and replace with `NativeAdView`.
    - find `GADNativeAd` and replace with `NativeAd`.
  - Open `Project_HOME/ios/Runner/ListTileNativeAdViewFactory.swift`, find and replace:
    - find `GADNativeAdView` and replace with `NativeAdView`.
    - find `GADNativeAd` and replace with `NativeAd`.
- Do a project clean. Remove pubspec.lock, ios/Podfile.lock.
- For iOS, you might also need to run `pod install --repo-update` from terminal to referesh the local pod repo. Important: Run this only after you have run the `flutter pub get` in your project root via terminal or from UI.
- Rest of configurations like configuration.json, ios project folders should remain same.
- Run and Launch your app on device.

On the wordpress admin panel:
- Remove existing plugin, and upload and activate your Houzi Rest Api version 1.4.6 plugin. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip) 


## Migration Guide for 1.4.5

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

Let's assume you simply want to update your houzi_package, updating to 1.4.5 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.5 and replace houzi_package in your existing project. 
- Download and update to Flutter 3.35.xx. [Flutter Download](../tools/flutter_setup).
- If you are upgrading from an older version to 1.4.5, you must also update your project for Android 15+ (API 36) and 16KB page size support:
  - Open Android Studio → SDK Manager, install Android SDK 36 (Android 15+), install latest Build Tools, and update NDK to version 29.0.13846066 or newer.
  
  - Open `Project_HOME/android/settings.gradle`, update AGP version:
    - `id "com.android.application" version '8.7.3' apply false`

  - Open `Project_HOME/android/gradle/wrapper/gradle-wrapper.properties`, update:
    - `distributionUrl=https\://services.gradle.org/distributions/gradle-8.12-all.zip`
  
  - Open `Project_HOME/android/app/build.gradle`, update:
    - find and set `compileSdkVersion 36`
    - find and set `minSdkVersion 24`
    - find and set `targetSdkVersion 36`
- Migrate iOS Project to minimum iOS 15 and make following changes:
  - Open `Project_HOME/ios/Podfile`, update:
    - `platform :ios, '15.0` at line number 2.
  - Open `Project_HOME/ios/Runner/HomeNativeAdViewFactory.swift`, find and replace:
    - find `GADNativeAdView` and replace with `NativeAdView`.
    - find `GADNativeAd` and replace with `NativeAd`.
  - Open `Project_HOME/ios/Runner/ListTileNativeAdViewFactory.swift`, find and replace:
    - find `GADNativeAdView` and replace with `NativeAdView`.
    - find `GADNativeAd` and replace with `NativeAd`.
- Do a project clean. Remove pubspec.lock, ios/Podfile.lock.
- For iOS, you might also need to run `pod install --repo-update` from terminal to referesh the local pod repo. Important: Run this only after you have run the `flutter pub get` in your project root via terminal or from UI.
- Rest of configurations like configuration.json, ios project folders should remain same.
- Run and Launch your app on device.

On the wordpress admin panel:
- Remove existing plugin, and upload and activate your Houzi Rest Api version 1.4.5 plugin. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip) 




## Migration Guide for 1.4.0.1

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

Let's assume you simply want to update your houzi_package, updating to 1.4.0.1 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.0.1 and replace houzi_package in your existing project. 
- Optionally download and update to Flutter 3.32.xx. [Flutter Download](../tools/flutter_setup).
- Upgrade the Kotlin Gradle plugin version to 2.1.21 by updating the line in android/settings.gradle if you have updated Flutter to version 3.32.x:
    - `id "org.jetbrains.kotlin.android" version "2.1.21" apply false // Required for Flutter 3.32.x compatibility`
- We added new hooks in hooks_v2.dart. So copy `Project_HOME/lib/hooks_v2.dart` and `Project_HOME/lib/main.dart` and replace both in your existing project. Then configure your hooks again. (Mandatory if you are updating.)
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.
- Do a project clean. Remove pubspec.lock, ios/Podfile.lock.
- For iOS, you might also need to run `pod install --repo-update` from terminal to referesh the local pod repo. Important: Run this only after you have run the `flutter pub get` in your project root via terminal or from UI.
- Run and Launch your app on device.

On the wordpress admin panel:
- Remove existing plugin, and upload and activate your Houzi Rest Api version 1.4.0.1 plugin. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip) 




## Migration Guide for 1.4.4

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

Let's assume you simply want to update your houzi_package, updating to 1.4.4 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.4 and replace houzi_package in your existing project. 
- Optionally download and update to Flutter 3.32.xx. [Flutter Download](../tools/flutter_setup).
- Upgrade the Kotlin Gradle plugin version to 2.1.21 by updating the line in android/settings.gradle if you have updated Flutter to version 3.32.x:
    - `id "org.jetbrains.kotlin.android" version "2.1.21" apply false // Required for Flutter 3.32.x compatibility`
- We added new hooks in hooks_v2.dart. So copy `Project_HOME/lib/hooks_v2.dart` and `Project_HOME/lib/main.dart` and replace both in your existing project. Then configure your hooks again. (Mandatory if you are updating.)
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.
- Do a project clean. Remove pubspec.lock, ios/Podfile.lock.
- For iOS, you might also need to run `pod install --repo-update` from terminal to referesh the local pod repo. Important: Run this only after you have run the `flutter pub get` in your project root via terminal or from UI.
- Run and Launch your app on device.

On the wordpress admin panel:
- Remove existing plugin, and upload and activate your Houzi Rest Api version 1.4.4 plugin. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip) 




## Migration Guide for 1.4.3.4

> **Important Notice:** If you are updating from version lower than 1.4.0, we recommend you to first perform the migration for 1.4.0, then do essentials listed in 1.4.2 migration and then perform migration to 1.4.3. Upgrading from 1.4.2 should be easy as below.

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

Let's assume you simply want to update your houzi_package, updating to 1.4.3.4 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.3.4 and replace houzi_package in your existing project.
- Important to copy ios/Runner/AppDelegate.swift from 1.4.3.4 and replace in your existing ios project in the same path. It adds support for deep-link when iOS app is in quit state. Also fixes double notification permission dialog. [Not required if old version is  1.4.3 or above]
- Optionally for update to android 35 open android/app/build.gradle and set `compileSdkVersion 35` and `targetSdkVersion 35`. It will require you to download android 35 sdk. 
- Optionally download and update to Flutter 3.29.xx. [Flutter Download](../tools/flutter_setup).
- Open your hooks_v2.dart file at `Project_HOME > lib > hooks_v2.dart` and fix follow imports.  [Not required if old version is 1.4.3 or above]
    - Replace Map Marker Data
      - Old `import 'package:houzi_package/models/map_marker_data.dart';`
      - New `import 'package:houzi_package/models/search/map_marker_data.dart';`
    - Replace Drawer Menu Item
      - Old `import 'package:houzi_package/models/drawer_menu_item.dart';`
      - New `import 'package:houzi_package/models/drawer/drawer_menu_item.dart';`
    - Add intl package import
      - `import 'package:intl/intl.dart';`
- Open `Project_HOME/android/app/src/main/kotlin/com/houzi/app/ApplicationClass.kt` and change its parent class from FlutterApplication to Application. Check `ApplicationClass.kt` from 1.4.3.4 for reference. (Note: Your package directory and hirarchy may vary).
- Open `android/app/build.gradle` and find the `implementation 'com.onesignal:OneSignal:5.1.20'` and change it to `implementation 'com.onesignal:OneSignal:5.1.26'` So it uses latest OneSignal library.
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.
- Do a project clean. Remove pubspec.lock, ios/Podfile.lock.
- For iOS, you might also need to run `pod install --repo-update` from terminal to referesh the local pod repo. Important: Run this only after you have run the `flutter pub get` in your project root via terminal or from UI.
- Run and Launch your app on device.

On the wordpress admin panel:
- Remove existing plugin, and upload and activate your Houzi Rest Api version 1.4.3.2 plugin. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip) 
- If you have not already, update to new rich api token for OneSignal. It requires new Rest API Key. Simply put, generate new rich api key and save to Houzi Rest Api plugin. Read Guide here: [Push Notification](../tools/push_notifications_integration).




