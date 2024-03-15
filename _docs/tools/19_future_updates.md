---
title: Upgrading with future updates (Migration)
category: Tools Setup
permalink: tools/upgrading_future_version
order: 19
---

Always make a backup before updating to the next version.


## Update to 1.3.9

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).
Let's assume you simply want to update your houzi_package, updating to 1.3.9 requires you following things:

- Always make a backup. (copy in separate folder or use git).
- Update Flutter to 3.19.XX.
- Copy `Project_HOME > packages > houzi_package` from 1.3.9 and replace houzi_package in your existing project.
- Copy new hooks_v2.dart and replace existing `Project_HOME > lib > hooks_v2.dart` (if you have made any changes to existing hooks_v2.dart, then you need to carefully review and migrate new changes from hooks_v2.dart into your existing hooks_v2.dart)
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Since Flutter 3.16, Plugin DSL is used to apply Gradle plugins. Migrate your project manually using [Deprecated imperative apply of Flutter's Gradle plugins](https://docs.flutter.dev/release/breaking-changes/flutter-gradle-plugin-apply). **OR**
- Alternatively, you can copy following files from houzi-1.3.9 to your existing project:
  - `Project_HOME > android > build.gradle`.
  - `Project_HOME > android > settings.gradle`.
  - `Project_HOME > android > app > build.gradle`.
  - `Project_HOME > android > gradle > wrapper > gradle-wrapper.properties`.
  > Note: Remember to re-write the **applicationId, versionCode** and **versionName** with your own app details in these copied files.
- Upgrade your Houzi Rest Api plugin to version 1.3.9. Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip)
- Copy translation files or at least copy over new translations from this release.
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.


## Update to 1.3.8

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).
Let's assume you simply want to update your houzi_package, updating to 1.3.8 requires you following things:

- Always make a backup. (copy in separate folder or use git)
- Update Flutter to 3.16.XX 
- Copy `Project_HOME > packages > houzi_package` from 1.3.8 and replace houzi_package in your existing project.
- Update the 'flutter_launcher_icons: 0.XX.X' with "flutter_launcher_icons: 0.13.1" in `Project_HOME > pubspec.yaml`.
- Copy new hooks_v2.dart and replace existing `Project_HOME > lib > hooks_v2.dart` (if you have made any changes to existing hooks_v2.dart, then you need to carefully review and migrate new changes from hooks_v2.dart into your existing hooks_v2.dart)
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Upgrade your wordpress plugin to version 1.3.8
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.


## Update to 1.3.7.1

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).
Let's assume you simply want to update your houzi_package, updating to 1.3.7.1 requires you following things:

- Always make a backup. (copy in separate folder or use git)
- Update Flutter to 3.13.XX 
- Copy `Project_HOME > packages > houzi_package` from 1.3.7.1 and replace houzi_package in your existing project.
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Upgrade your wordpress plugin to version 1.3.7.1
- For in-app-purchase based membership, please follow guide here: [Docs](https://houzi-docs.booleanbites.com/tools/in_app_purchase).
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.


## Update to 1.3.7

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).
Let's assume you simply want to update your houzi_package, updating to 1.3.7 requires you following things:

- Always make a backup. (copy in separate folder or use git)
- Update Flutter to 3.13.XX 
- Copy `Project_HOME > packages > houzi_package` from 1.3.7 and replace houzi_package in your existing project.
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Upgrade your wordpress plugin to version 1.3.7
- For in-app-purchase based membership, please follow guide here: [Docs](https://houzi-docs.booleanbites.com/tools/in_app_purchase).
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.


## Update to 1.3.5

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).
Let's assume you simply want to update your houzi_package, updating to 1.3.5 requires you following things:

- Always make a backup. (copy in separate folder or use git)
- Update Flutter to 3.10.0+ 
- Copy `Project_HOME > packages > houzi_package` from 1.3.5 and replace houzi_package in your existing project.
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)

##### If you're upgrading from older version than 1.3.0.
- Update Android targetSdkVersion to 33 in following file:  `PROJECT_HOME/android/app/build.gradle` and look for `targetSdkVersion` and change to 33
- Migrate hooks.dart to hooks_v2.dart. HooksV2 is more simpler and fail safe. We kept the name of the hooks same, just make sure you're returning the correct data like you returned in older hooks.dart.
- then You need to enable Flutter Deeplinking in Android main Activity in following file:  `PROJECT_HOME/android/app/src/main/AndroidManifest.xml` and add this line `<meta-data android:name= "flutter_deeplinking_enabled" android:value="true" />` above `<intent-filter android:autoVerify="true">`.
- Enable Flutter Deeplinking in iOS info.plist in following file:  `PROJECT_HOME/ios/Runner/Info.plist` and add following line.
  ```
  <key>FlutterDeepLinkingEnabled</key>
    <true/>
  ```
  Then go to iOS Runner.entitlements in following file:  `PROJECT_HOME/ios/Runner/Runner.entitlements` and add following line:
  ```
  <key>com.apple.developer.associated-domains</key>
	<array>
		<string>applinks:domain.com</string>
	</array>
  ```
  Replace domain.com with your domain.
- Open file at `Project_HOME/android/build.gradle` and update Kotlin plugin version to `'1.8.22'` at line # 2. (e.g `ext.kotlin_version = '1.8.22'`)

- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.

## Update to 1.3.0

Version 1.3.0 is a major upgrade. We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).
Let's assume you simply want to update your houzi_package, updating to 1.3.0 requires you following things:

- Always make a backup. (copy in separate folder or use git)
- Update Flutter to 3.10.0+ 
- Copy `Project_HOME > packages > houzi_package` from 1.3.0 and replace houzi_package in your existing project.
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Migrate hooks.dart to hooks_v2.dart. HooksV2 is more simpler and fail safe. We kept the name of the hooks same, just make sure you're returning the correct data like you returned in older hooks.dart.
- Update Android targetSdkVersion to 33 in following file:  `PROJECT_HOME/android/app/build.gradle` and look for `targetSdkVersion` and change to 33
- Enable Flutter Deeplinking in Android main Activity in following file:  `PROJECT_HOME/android/app/src/main/AndroidManifest.xml` and add this line `<meta-data android:name= "flutter_deeplinking_enabled" android:value="true" />` above `<intent-filter android:autoVerify="true">`.
- Enable Flutter Deeplinking in iOS info.plist in following file:  `PROJECT_HOME/ios/Runner/Info.plist` and add following line.
  ```
  <key>FlutterDeepLinkingEnabled</key>
    <true/>
  ```
  Then go to iOS Runner.entitlements in following file:  `PROJECT_HOME/ios/Runner/Runner.entitlements` and add following line:
  ```
  <key>com.apple.developer.associated-domains</key>
	<array>
		<string>applinks:domain.com</string>
	</array>
  ```
  Replace domain.com with your domain.
- Open file at `Project_HOME/android/build.gradle` and update Kotlin plugin version to `'1.8.22'` at line # 2. (e.g `ext.kotlin_version = '1.8.22'`)

- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.



