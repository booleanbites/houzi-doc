---
title: Upgrading with future updates
category: Tools Setup
permalink: tools/upgrading_future_version
order: 19
---

Always make a backup before updating to the next version.

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

## Update to 1.2.0

Version 1.2.0 is a major upgrade. We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).
Let's assume you simply want to update your houzi_package, updating to 1.2.0 requires you following things:

- Always make a backup. (copy in separate folder or use git)
- Update Flutter to 3.7.0+ 
- Copy `Project_HOME > packages > houzi_package` from 1.2.0 and replace houzi_package in your existing project.
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Migrate hooks.dart to hooks_v2.dart. HooksV2 is more simpler and fail safe. We kept the name of the hooks same, just make sure you're returning the correct data like you returned in older hooks.dart.
- Upgrade your dart version to 2.18 or above, for null-safety support. Open your file at path: `PROJECT_HOME / pubspec.yaml` and change the sdk version to `sdk: ">=2.18.2 <3.0.0"`. 
  
If you're updating from versions older than 1.1.5_1, then you'll need to:
- Delete file: `Project_HOME/l10n.yaml`
- Update Android targetSdkVersion to 31 in following file:  `PROJECT_HOME/android/app/build.gradle` and look for `targetSdkVersion` and change to 31
- Add exported attribute in main Activity following file:  `PROJECT_HOME/android/app/src/main/AndroidManifest.xml` and look for `<Activity` tag and add an attribute `android:exported="true"`
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.

