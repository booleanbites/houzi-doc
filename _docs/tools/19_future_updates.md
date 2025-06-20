---
title: Migration Guide
category: Tools Setup
permalink: tools/upgrading_future_version
order: 20
---

Always make a backup before updating to the next version.


## Migration Guide for 1.4.5

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

Let's assume you simply want to update your houzi_package, updating to 1.4.5 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.5 and replace houzi_package in your existing project. 
- Optionally download and update to Flutter 3.32.xx. [Flutter Download](../tools/flutter_setup).
- Upgrade the Kotlin Gradle plugin version to 2.1.21 by updating the line in android/settings.gradle if you have updated Flutter to version 3.32.x:
    - `id "org.jetbrains.kotlin.android" version "2.1.21" apply false // Required for Flutter 3.32.x compatibility`
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.
- Do a project clean. Remove pubspec.lock, ios/Podfile.lock.
- For iOS, you might also need to run `pod install --repo-update` from terminal to referesh the local pod repo. Important: Run this only after you have run the `flutter pub get` in your project root via terminal or from UI.
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




