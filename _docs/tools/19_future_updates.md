---
title: Upgrading with future updates (Migration)
category: Tools Setup
permalink: tools/upgrading_future_version
order: 19
---

Always make a backup before updating to the next version.

## Update to 1.4.0

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).
Let's assume you simply want to update your houzi_package, updating to 1.4.0 requires you following things:

- Always make a backup. (copy in separate folder or use git).
- Update Flutter to 3.22.XX.
- Copy `Project_HOME > packages > houzi_package` from 1.4.0 and replace houzi_package in your existing project.
- Copy new hooks_v2.dart and replace existing `Project_HOME > lib > hooks_v2.dart` (if you have made any changes to existing hooks_v2.dart, then you need to carefully review and migrate new changes from hooks_v2.dart into your existing hooks_v2.dart)
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Upgrade your Houzi Rest Api plugin to version 1.4.0 download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip)
- Copy translation files or at least copy over new translations from this release.
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.

There are some additional configurations if you want to run your project on new **Android Studio Jellyfish**.

1. Go to project **settings.gradle** file by following this path:  

    `Project_HOME > android > settings.gradle`  

    Replace the **plugins** block with the following one:

    ```groovy
    plugins {
        id "dev.flutter.flutter-plugin-loader" version "1.0.0"
        id "com.android.application" version '8.4.0' apply false
        id "org.jetbrains.kotlin.android" version '1.9.23' apply false
        id "com.google.gms.google-services" version "4.3.8" apply false
    }
    ```

2. Go to app **build.gradle**  file by following this path:  
    
    `Project_HOME > android > app > build.gradle`
    
    Perform following modifications:

    a. Add your **namespace** in *android block* as following:

    ```groovy
        android {
            namespace "com.example.app"
            ...
        }
    ```

    b. Replace the **release** block in the **buildTypes** block with the following:

    ```groovy
        release {
            signingConfig signingConfigs.release
            minifyEnabled true

            proguardFiles(
                    getDefaultProguardFile("proguard-android-optimize.txt"),
                    // List additional ProGuard rules for the given build type here. By default,
                    // Android Studio creates and includes an empty rules file for you (located
                    // at the root directory of each module).
                    "proguard-rules.pro"
            )
        }
    ```

    c. Add following **compileOptions** block and **kotlinOptions** block in the *android block* as following:

    ```groovy
        android {
            ...
            compileOptions {
                // Flag to enable support for the new language APIs
                coreLibraryDesugaringEnabled true
                // Sets Java compatibility to Java 8
                sourceCompatibility JavaVersion.VERSION_1_8
                targetCompatibility JavaVersion.VERSION_1_8
            }
            kotlinOptions {
                jvmTarget = "1.8"
            }
            ...
        }
    ```

    d. Add following dependency in *dependencies block*

    ```groovy
        dependencies {
            ...
                coreLibraryDesugaring 'com.android.tools:desugar_jdk_libs:2.0.3'
            ...
        }
    ```

    e. Replace the *1.9.10* with **1.9.23** in following dependency of dependencies block

    ```groovy
        implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk7:1.9.10" [OLD]
        implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk7:1.9.23" [UPDATED]
    ```

3. Copy the file **progurad-rules.pro** from the `PROJECT_HOME > android > app > progurad-rules.pro` and paste it in the app folder (path: `PROJECT_HOME > android > app`) of your project.

4. Go to app **AndroidManifest.xml** file by following this path:  

    `Project_HOME > android > app > src  > main > AndroidManifest.xml`  
    
    Perform following modifications:

    a. Add following code line in the <manifest> tag at the start of the file:
    ```xml   
        xmlns:tools="http://schemas.android.com/tools"
    ```
    e.g.   
    *Before:
    ```xml   
        <manifest
            xmlns:android="http://schemas.android.com/apk/res/android"
            package="com.example.app">
    ```

    *After:
    ```xml   
        <manifest
            xmlns:android="http://schemas.android.com/apk/res/android"
            xmlns:tools="http://schemas.android.com/tools"
            package="com.example.app">
    ```

    b. Just before the closing of <application> tag add the following block of code:
    ```xml   
        <property
            android:name="android.adservices.AD_SERVICES_CONFIG"
            android:resource="@xml/gma_ad_services_config"
            tools:replace="android:resource"/>
    ```

5. Go to **gradle-wrapper.properties** file by following this path:   

    `Project_HOME > android > gradle > wrapper > gradle-wrapper.properties` 
    
    Replace the distributionUrl with following one:

    https\://services.gradle.org/distributions/gradle-8.6-all.zip

6. Go to package**pubspec.yaml** file by following this path:    

    `Project_HOME > packages > houzi_package > pubspec.yaml` 

    Update the following dependencies accordingly:  
    
    ```yaml
        google_mobile_ads: 5.0.0  
        webview_flutter: 4.7.0  
        flutter_local_notifications: 17.1.1
    ```

7. Go to the project **build.gradle** file by following this path:  
    
    `Project_HOME > android > build.gradle`  
      
    Add following code below the **allprojects** block
  ```groovy
      subprojects {
          afterEvaluate { project ->
              if (project.hasProperty('android')) {
                  project.android {
                      if (namespace == null) {
                          namespace project.group
                      }
                  }
              }
          }
      }
```

We have provide support for the push notifications in the Houzi 1.4.0 release. You need to perform following configurtion to enable push notifications in your existing apps.

- You need to integrate the push notifications. For more information [Push Notifications Integration](.../push_notifications_integration). 
- Copy the **MainActivity**, **ApplicationClass** and **NotificationServiceExtension** files from Houzi 1.4.0 to your existing project. 
    - File path: `PROJECT_HOME > android > app > src > main > kotlin > com > houzi > app`
    - Destination file path: `PROJECT_HOME > android > app > src > main > kotlin > your > package > name > all_kotlin_files`.
- Copy the **AndroidMenifest.xml** file from Houzi 1.4.0 to your existing project. Path: `PROJECT_HOME > android > app > src > main`.
- Remember to rename the app name in *AndroidMenifest.xml*.
- Remember to replace the package declaration in kotlin files, i.e. replace com.houzi.app to your.package.name.
- If you have made any changes to existing *MainActivity* and *AndroidMenifest.xml*, then you need to carefully review and migrate new changes from these files into your existing ones.
- Add following dependency into the dependency block of the **build.gradle** file. File path `PROJECT_HOME > android > app > build.gradle`.

```groovy
  implementation 'com.onesignal:OneSignal:5.1.13'
  ```
- Follow the [iOS setup guide](https://documentation.onesignal.com/docs/flutter-sdk-setup#2-ios-setup).
- Copy the **AppDelegate.swift** from Houzi 1.4.0 to your existing project. File path: `PROJECT_HOME > ios > Runner > AppDelegate.swift`. If you have made any changes to existing *AppDelegate.swift*, then you need to carefully review and migrate new changes from this file into your AppDelegate.swift file.
- Remember to replace the **ONE_SIGNAL_APP_ID** with yours in the AppDelegate.swift.
- Set the minimum deployment iOS to 14.0 in *Runner*, *OneSignalNotificationServiceExtension* and *Podfile*.

## Update to 1.3.9.1

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).
Let's assume you simply want to update your houzi_package, updating to 1.3.9.1 requires you following things:

- Always make a backup. (copy in separate folder or use git).
- Update Flutter to 3.19.XX.
- Copy `Project_HOME > packages > houzi_package` from 1.3.9.1 and replace houzi_package in your existing project.
- Copy new hooks_v2.dart and replace existing `Project_HOME > lib > hooks_v2.dart` (if you have made any changes to existing hooks_v2.dart, then you need to carefully review and migrate new changes from hooks_v2.dart into your existing hooks_v2.dart)
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Since Flutter 3.16, Plugin DSL is used to apply Gradle plugins. Migrate your project manually using [Deprecated imperative apply of Flutter's Gradle plugins](https://docs.flutter.dev/release/breaking-changes/flutter-gradle-plugin-apply). **OR**
- Alternatively, you can copy following files from houzi-1.3.9 to your existing project:
  - `Project_HOME > android > build.gradle`.
  - `Project_HOME > android > settings.gradle`.
  - `Project_HOME > android > app > build.gradle`.
  - `Project_HOME > android > gradle > wrapper > gradle-wrapper.properties`.
  > Note: Remember to re-write the **applicationId, versionCode** and **versionName** with your own app details in these copied files.
- Upgrade your Houzi Rest Api plugin to version 1.3.9.1 Download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip)
- Copy translation files or at least copy over new translations from this release.
- Add the line and telegram icon from `Project_HOME > assets > icon` and paste to same location. Don't forget to list them in `Project_HOME > pubspec.yaml` along with other icons.
- Add the PrivacyInfo.xcprivacy file from 1.3.9.1 Xcode project. It can be found here: `Project_Home/ios/Runner/PrivacyInfo.xcprivacy`. Simply drag the file and drop in your Xcode project.
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.


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



