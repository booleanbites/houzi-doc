---
title: Migration Guide
category: Tools Setup
permalink: tools/upgrading_future_version
order: 19
---

Always make a backup before updating to the next version.

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




## Migration Guide for 1.4.2

> **Important Notice:** If you are updating from version lower than 1.4.0, we recommend you to first perform the migration for 1.4.0, then migrate to 1.4.2.

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

Let's assume you simply want to update your houzi_package, updating to 1.4.2 requires you following things:

- Always make a backup. (copy in separate folder or use git).
- Copy `Project_HOME > packages > houzi_package` from 1.4.2 and replace houzi_package in your existing project.
- Copy new hooks_v2.dart and replace existing `Project_HOME > lib > hooks_v2.dart` (if you have made any changes to existing hooks_v2.dart, then you need to carefully review and migrate new changes from hooks_v2.dart into your existing hooks_v2.dart)
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Upgrade your Houzi Rest Api plugin to version 1.4.2 download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip)
- Copy translation files or at least copy over new translations from this release.

- Add following code into the subprojects block, below the code line `rootProject.buildDir = '../build`, of the **build.gradle** file. File path `PROJECT_HOME > android > build.gradle`.

```groovy
  subprojects {
    project.buildDir = "${rootProject.buildDir}/${project.name}"

    // add this line for onesignal_flutter to work in android device
    afterEvaluate {
        android {
            compileSdkVersion 34
        }
    }
}
  ```

- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.
- Enable Direct Messages if required. Read Guide here: [Direct Messages](../tools/direct_messages).

## Migration Guide for 1.4.0

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again).

> **Easier Path:** Although we've listed almost all the steps to migrate your existing Flutter Project to push notification and Android Gradle Plugin migration. We think, configuring new project in 1.4.0 may be easier path than doing the migration.

Let's assume you simply want to update your houzi_package, updating to 1.4.0 requires you following things:

- Always make a backup. (copy in separate folder or use git).
- Update Flutter to 3.22.XX.
- Copy `Project_HOME > packages > houzi_package` from 1.4.0 and replace houzi_package in your existing project.
- Copy new hooks_v2.dart and replace existing `Project_HOME > lib > hooks_v2.dart` (if you have made any changes to existing hooks_v2.dart, then you need to carefully review and migrate new changes from hooks_v2.dart into your existing hooks_v2.dart)
- Copy new main.dart and replace existing `Project_HOME > lib > main.dart` (if you have made any changes to existing main.dart, then you need to carefully review and migrate new changes from main.dart into your existing main.dart)
- Upgrade your Houzi Rest Api plugin to version 1.4.0 download from here: [Houzi Rest Api](https://github.com/booleanbites/houzi-rest-api/releases/latest.zip)
- Copy translation files or at least copy over new translations from this release.
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.
- Configure your android project to do Android Gradle Pluging migration explained below.
- Push Notification related configurations explained below.

#### Push Notification with OneSignal
We have provide support for the push notifications in the Houzi 1.4.0 release. You need to perform following configurtion to enable push notifications in your existing apps.

- You need to integrate the push notifications. For more information [Push Notifications Integration](push_notifications_integration). 
- Copy the **MainActivity**, **ApplicationClass** and **NotificationServiceExtension** files from Houzi 1.4.0 to your existing project. 
    - File path: `PROJECT_HOME > android > app > src > main > kotlin > com > houzi > app`
    - Destination file path: `PROJECT_HOME > android > app > src > main > kotlin > your > package > name > all_kotlin_files`.
- Copy the **AndroidMenifest.xml** file from Houzi 1.4.0 to your existing project. Path: `PROJECT_HOME > android > app > src > main`.
- Remember to set package name and the app name in *AndroidMenifest.xml*.
- Remember to replace the package declaration in kotlin files, i.e. replace com.houzi.app to your.package.name.
- Add new key value to strings.xml here at `PROJECT_HOME > android > app > src > main > res > values > strings.xml` as below
  
 ```xml
 <string name="onesignal_app_id">YOUR_ONESIGNAL_APP_ID_OR_EMPTY</string>
 ``` 

- If you have made any changes to existing *MainActivity* and *AndroidMenifest.xml*, then you need to carefully review and migrate new changes from these files into your existing ones.
- Add following dependency into the dependency block of the **build.gradle** file. File path `PROJECT_HOME > android > app > build.gradle`.

```groovy
  implementation 'com.onesignal:OneSignal:5.1.13'
  ```
- Follow the [iOS setup guide](https://documentation.onesignal.com/docs/flutter-sdk-setup#2-ios-setup). It'll help you add an extension target to your iOS project for one signal notifications.
- Copy the **AppDelegate.swift** from Houzi 1.4.0 to your existing project. File path: `PROJECT_HOME > ios > Runner > AppDelegate.swift`. If you have made any changes to existing *AppDelegate.swift*, then you need to carefully review and migrate new changes from this file into your AppDelegate.swift file.
- Remember to replace the **ONE_SIGNAL_APP_ID** with yours in the AppDelegate.swift.
- Set the minimum deployment iOS to 14.0 in *Runner*, *OneSignalNotificationServiceExtension* and *Podfile*.

#### Migration to Android Studio Jellyfish
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



