---
title: Upgradation Guide for Android Studio Jellyfish | 2023.3.1
category: Tools Setup
permalink: tools/upgradation_guide_for_android_studio_jelly_fish
order: 23
---

Please perform the following upgradations to run your project on new Android Studio Jellyfish:

1. Go to project **settings.gradle** file by following this path:  

    `PROJECT-NAME/android/settings.gradle`  

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
    
    `PROJECT-NAME/android/app/build.gradle`
    
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

    `PROJECT-NAME/android/app/src/main/AndroidManifest.xml`  
    
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

    `PROJECT-NAME/android/gradle/wrapper/gradle-wrapper.properties` 
    
    Replace the distributionUrl with following one:

    https\://services.gradle.org/distributions/gradle-8.6-all.zip

6. Go to package**pubspec.yaml** file by following this path:    

    `PROJECT-NAME/packages/houzi_package/pubspec.yaml` 

    Update the following dependencies accordingly:  
    
    ```yaml
        google_mobile_ads: 5.0.0  
        webview_flutter: 4.7.0  
        flutter_local_notifications: 17.1.1
    ```

7. Go to the project **build.gradle** file by following this path:  
    
    `PROJECT-NAME/android/build.gradle`  
     
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
    
8. Delete the **pubspec.lock** file (path: `PROJECT-NAME/pubspec.lock`).

9. Perform Flutter clean from top menu as
    `Tools > Flutter > Flutter Clean`.

10. Run the app.