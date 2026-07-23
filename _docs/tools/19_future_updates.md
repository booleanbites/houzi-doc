---
title: Migration Guide
category: Tools Setup
permalink: tools/upgrading_future_version
order: 20
---

Always make a backup before updating to the next version.


## Migration Guide for 1.4.8

**1.4.8** introduces Houzi AI (AI-powered search, AI-first home, and ask-the-listing), upgrades all Android and iOS dependencies to their latest versions, and migrates the iOS project from **CocoaPods** to **Swift Package Manager (SPM)**.

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

> **Important — iOS is different this time.** This release moves iOS from CocoaPods to Swift Package Manager. Hand-migrating an existing `ios` folder (removing the Podfile, de-integrating CocoaPods, and re-wiring OneSignal and Google Maps through SPM) is highly technical and error-prone, so we do **not** ask you to migrate it. Instead, **replace your `ios` folder with the one we provide in 1.4.8 and reconfigure it** with your own app details (see the iOS section below). This also raises the **minimum iOS version to 15**.

Let's assume you simply want to update your houzi_package, updating to 1.4.8 requires the following:

- Always make a backup. (copy in a separate folder or use git).
- Download and update to **Flutter 3.44.xx**. [Flutter Download](../tools/flutter_setup).
- Copy `Project_HOME > packages > houzi_package` from 1.4.8 and replace houzi_package in your existing project. This brings Houzi AI, the upgraded dependencies, and all related code changes (no app-level hook changes are required this release).
- Open your **app-level** `Project_HOME/pubspec.yaml` and add the SPM-compatible Google Maps iOS implementation under `dependencies:`
  ```yaml
  google_maps_flutter_ios_sdk9: 2.18.6
  ```
  > This must live in your **app-level** `pubspec.yaml` (not in houzi_package). Flutter only honors an alternative plugin implementation when it is a direct app dependency; placed in houzi_package it is ignored and iOS silently falls back to the CocoaPods Google Maps. It requires a minimum iOS deployment target of **15**.
- Update your app localization for the new AI features. The Houzi AI screens (AI Search, voice search, AI matches, status messages, example prompts, etc.) rely on new `ai_*` localization keys added in 1.4.8. These live in your **app-level** `Project_HOME/assets/localization/*.json` files, so they do **not** come with houzi_package — if you skip this step, the AI screens will display raw keys (e.g. `ai_search`) instead of text.
  - If you have **not** customized your localization strings: copy the updated `Project_HOME/assets/localization/*.json` files from 1.4.8 and replace yours.
  - If you **have** customized them: merge the new `ai_*` keys from each 1.4.8 file into your existing `*.json` files so your customizations are preserved.
  - New keys were added to every bundled language: `en, ar, am, es, fa, fr, ku, pt, ro, ru, tr, ur`.
- **(Optional — only if you build with AI coding agents.)** Copy `Project_HOME > .agents > skills > houzi` directory and the AI assistant config files (`Project_HOME > CLAUDE.md`, `Project_HOME > .cursorrules`, `Project_HOME > .github > copilot-instructions.md`, and `Project_HOME > AGENTS.md`) from 1.4.8 to your own project root. This is only needed if you want to leverage the built-in [AI Agent Skill](../ai-agents/houzi_skill) in AI coding assistants (such as Antigravity, Cursor, Claude Code, or GitHub Copilot); you can skip it entirely otherwise. The skill was updated in 1.4.8 for the new AI features.

#### Android

- Open `Project_HOME/android/settings.gradle`, update the Android Gradle Plugin version:
  - `id "com.android.application" version '8.13.2' apply false`
- Open `Project_HOME/android/gradle.properties`, add the following lines:
  ```properties
  org.gradle.caching=true
  # This builtInKotlin flag was added automatically by Flutter migrator
  android.builtInKotlin=false
  # This newDsl flag was added automatically by Flutter migrator
  android.newDsl=false
  ```
- Open `Project_HOME/android/app/src/main/AndroidManifest.xml`, add the microphone permission (required for AI voice search):
  ```xml
  <uses-permission android:name="android.permission.RECORD_AUDIO" />
  ```
  and, inside the existing `<queries>` block, add the speech recognizer intent (required on Android 11+):
  ```xml
  <intent>
      <action android:name="android.speech.RecognitionService" />
  </intent>
  ```
- Update the Google Mobile Ads native ad factories for the new `google_mobile_ads` API. Open both `Project_HOME/android/app/src/main/kotlin/<your app package>/HomeNativeAdFactory.kt` and `ListTileNativeAdFactory.kt`, and in each file:
  - Replace the import:
    - Old: `import io.flutter.plugins.googlemobileads.GoogleMobileAdsPlugin`
    - New: `import io.flutter.plugins.googlemobileads.NativeAdFactory`
  - Replace the class declaration:
    - Old: `... : GoogleMobileAdsPlugin.NativeAdFactory {`
    - New: `... : NativeAdFactory {`

  (`MainActivity.kt` needs no change; its `registerNativeAdFactory(...)` calls resolve once the factories implement the new interface.)

#### iOS (replace & reconfigure)

Because iOS moved to Swift Package Manager, **replace** your `ios` folder instead of migrating it:

- Copy the `Project_HOME/ios` folder from 1.4.8 and replace the `ios` folder in your existing project.
- Reconfigure it with your own app details:
  - **Bundle identifier** — [Change App Identifier / Bundle ID](../app-setup/change_app_identifier)
  - **App display name** — [Change App Display Name](../app-setup/change_app_display_name)
  - **App icon** — [Change App Icon](../app-setup/change_app_icon)
  - **Signing** — set your Team and provisioning profiles in Xcode. [Xcode Setup](../tools/xcode_setup)
  - **Firebase** — replace `ios/Runner/GoogleService-Info.plist` with your own.
  - **Google Maps API key** — in `ios/Runner/AppDelegate.swift`, set your key in `GMSServices.provideAPIKey("your-maps-api-key")`.
  - **OneSignal App ID** — in `ios/Runner/AppDelegate.swift`, set `ONE_SIGNAL_APP_ID`.
  - **AdMob** — set your `GADApplicationIdentifier` in `ios/Runner/Info.plist`.
  - **Social sign-in** — reconfigure your URL schemes in `ios/Runner/Info.plist` and follow each provider's guide:
    - [Sign in with Apple](../tools/setup_apple_signin)
    - [Facebook Sign-in](../tools/setup_facebook_signin)
    - [Google Sign-in](../tools/setup_google_signin)
- The provided `ios` folder already includes the full SPM setup, the OneSignal Notification Service Extension wired through SPM (linked as `OneSignalExtension`, Do Not Embed), and the microphone/speech-recognition usage descriptions. There is **no `Podfile`** — do not run `pod install`.

#### Finish

- Do a project clean. Remove `pubspec.lock` (there is no `ios/Podfile.lock` anymore once you use the provided `ios` folder).
- Run `flutter pub get`.
- Run and launch your app on a device.

On the wordpress admin panel:
- Remove existing plugin, and upload and activate your Houzi Rest Api version 1.4.8 plugin. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip)


## Migration Guide for 1.4.7.2

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

> If you are upgrading from an older version than 1.4.7.1, you must follow the previous migration guides below.

Let's assume you simply want to update your houzi_package, updating to 1.4.7.2 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.7.2 and replace houzi_package in your existing project. 
- Open hooks_v2.dart at `Project_HOME > lib > hooks_v2.dart` and configure `getValuedFeatureDesignHook()` to return `'v2'` if you want to switch from the horizontal scroll layout to the new 3-column grid design for bedrooms, bathrooms, etc. on the property details page. Note that when configuring or adding a new hook in `lib/hooks_v2.dart`, you must also register it in `lib/main.dart` inside the `hooksMap` by adding:
  ```dart
  hooksMap["valuedFeatureDesignHook"] = v2Hooks.getValuedFeatureDesignHook();
  ```
- Copy `Project_HOME > .agents > skills > houzi` directory and all AI skill-related configuration files (`Project_HOME > claude.md`, `Project_HOME > .cursorrules`, `Project_HOME > .github > copilot-instructions.md` and `Project_HOME > AGENTS.md`) from 1.4.7.2 to your own project root if you want to leverage the built-in [AI Agent Skill](../ai-agents/houzi_skill) in AI coding assistants (such as Antigravity, Cursor, Claude Code, or GitHub Copilot).
- Do a project clean. Remove pubspec.lock, ios/Podfile.lock.
- Rest of configurations like configurations.json, android/ios folders should remain same.
- Run and Launch your app on device.

On the wordpress admin panel:
- Remove existing plugin, and upload and activate your Houzi Rest Api version 1.4.7 plugin. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip)

## Migration Guide for 1.4.7.1

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

> If you are upgrading from an older version than 1.4.7, you must follow _Migration Guide 1.4.5_ to update your project for Android 15+ (API 36) and 16KB page size support.

Let's assume you simply want to update your houzi_package, updating to 1.4.7.1 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Open `Project_HOME/android/app/src/main/AndroidManifest.xml` and remove the permission `android.permission.READ_EXTERNAL_STORAGE`.
- Copy `Project_HOME > packages > houzi_package` from 1.4.7.1 and replace houzi_package in your existing project. 
- Download and update to Flutter 3.41.xx. [Flutter Download](../tools/flutter_setup).
- Open AppDelegate.swift at `Project_HOME/ios/Runner/AppDelegate.swift` and find
        `let controller = window.rootViewController as! FlutterViewController`
        replace with
        `let controller = window?.rootViewController as! FlutterViewController` //Notice the ? after window
- Do a project clean. Remove pubspec.lock, ios/Podfile.lock.
- For iOS, you might also need to run `pod install --repo-update` from terminal to referesh the local pod repo. Important: Run this only after you have run the `flutter pub get` in your project root via terminal or from UI.
- Rest of configurations like ios project folders should remain same.
- Run and Launch your app on device.

On the wordpress admin panel:
- Remove existing plugin, and upload and activate your Houzi Rest Api version 1.4.7 plugin. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip)

## Migration Guide for 1.4.7

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

> If you are upgrading from an older version than 1.4.7, you must follow _Migration Guide 1.4.5_ to update your project for Android 15+ (API 36) and 16KB page size support.

Let's assume you simply want to update your houzi_package, updating to 1.4.7 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.7 and replace houzi_package in your existing project. 
- Download and update to Flutter 3.41.xx. [Flutter Download](../tools/flutter_setup).
- Copy `Project_HOME/android/app/src/main/res/drawable/download_icon.xml` to your project in the same location.
- Copy `Project_HOME/assets/icon/compass_icon.png` to your project in the same location.
- Open AppDelegate.swift at `Project_HOME/ios/Runner/AppDelegate.swift` and find
        `let controller = window.rootViewController as! FlutterViewController`
        replace with
        `let controller = window?.rootViewController as! FlutterViewController` //Notice the ? after window
- Open your hooks_v2.dart file at `Project_HOME > lib > hooks_v2.dart` and copy and paste the following hooks code from following link:
  - [CustomSearchWebParamsHook](/hooks-widgets/custom_search_web_params)
  - [Houzi Map Provider Hook](/hooks-widgets/houzi_map_provider_hook)
  - [OSM Geo Admin Email Hook](/hooks-widgets/osm_geo_admin_email_hook)
  - [MapView Initial Location Hook](/hooks-widgets/map_view_initial_location_hook)
  - [Map Box Api Key Hook](/hooks-widgets/map_box_api_key_hook)
  - Additionally, register these hooks inside `hooksMap` in `Project_HOME/lib/main.dart` by adding:
  ```dart
  hooksMap["customSearchWebParamsHook"] = v2Hooks.getCustomSearchWebParamsHook();
  hooksMap["houziMapProviderHook"] = v2Hooks.getHouziMapProviderHook();
  hooksMap["osmGeoAdminEmailHook"] = v2Hooks.getOsmGeoAdminEmailHook();
  hooksMap["mapViewInitialLocationHook"] = v2Hooks.getMapViewInitialLocationHook();
  hooksMap["mapBoxApiKeyHook"] = v2Hooks.getMapBoxApiKeyHook();
  ```
- Open `Project_HOME/android/settings.gradle`, update to these latest:
  - `id "com.android.application" version '8.11.1' apply false`
  - `id "org.jetbrains.kotlin.android" version '2.2.20' apply false`
  - `id "com.google.gms.google-services" version "4.4.2" apply false`
- Open `Project_HOME/android/gradle/wrapper/gradle-wrapper.properties`, update your current to this:
  - `distributionUrl=https\://services.gradle.org/distributions/gradle-8.14-all.zip`
- Open `Project_HOME/android/app/build.gradle`, update the following dependencies:
  ```gradle
  dependencies {
      coreLibraryDesugaring 'com.android.tools:desugar_jdk_libs:2.1.5'

      implementation 'com.google.firebase:firebase-analytics:22.5.0'
      implementation 'com.google.android.gms:play-services-ads:24.1.0'

      // We commented this out because we are using minSdk 26 (Android 8) which is above 21,
      // so Android handles multidex automatically. Also this is old support library which
      // is no longer maintained by Google and conflicts with AndroidX.
      // If you ever need multidex library, use androidx.multidex:multidex:2.0.1 instead.
      // implementation 'com.android.support:multidex:1.0.3'

      implementation 'androidx.cardview:cardview:1.0.0'
      implementation 'androidx.appcompat:appcompat:1.7.0'
      implementation 'com.google.android.play:integrity:1.4.0'
      implementation 'androidx.browser:browser:1.8.0'
      implementation 'androidx.activity:activity:1.10.1'
      implementation 'com.onesignal:OneSignal:5.1.26'
  }
  ```
- Open `Project_HOME/android/gradle.properties`, remove `android.enableR8=true`, because it is deprecated now.
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

> If you are upgrading from an older version than 1.4.5, you must follow _Migration Guide 1.4.5_ to update your project for Android 15+ (API 36) and 16KB page size support.

Let's assume you simply want to update your houzi_package, updating to 1.4.6 requires following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.6 and replace houzi_package in your existing project. 
- Download and update to Flutter 3.35.xx. [Flutter Download](../tools/flutter_setup).
- Copy `Project_HOME/android/app/src/main/res/drawable/download_icon.xml` to your project in the same location.
- Open AppDelegate.swift at `Project_HOME/ios/Runner/AppDelegate.swift` and find
        `let controller = window.rootViewController as! FlutterViewController`
        replace with
        `let controller = window?.rootViewController as! FlutterViewController` //Notice the ? after window
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




## Migration Guide for 1.4.4.1

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




