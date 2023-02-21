---
title: Upgrading with future updates
category: Tools Setup
permalink: tools/upgrading_future_version
order: 19
---

Always make a backup before updating to the next version.


## Update to 1.1.5_1

We always assume, you haven't made changes to files in houzi_package. If you made changes in your houzi_package then you'll need to move over those manually (again). Let's assume you simply want to update your houzi_package, updating to 1.1.5_1 requires you following things:

- Always make a backup. (copy in separate folder or use git)
- Copy `Project_HOME > packages > houzi_package` from 1.1.5_1 and replace houzi_package in your existing project.
- We added two price formatting hooks. Open newer hooks file `Project_HOME > lib > Hooks.dart` and find class `CustomMethodsHook` at bottom of the file. This class contains two methods `getPriceFormatterHook()` and `getCompactPriceFormatterHook()`. Copy this `CustomMethodsHook` class and paste to your own hooks class.
- You also need to link these new hooks in main.dart by opening file `Project_HOME > lib > main.dart` and add these hooks to hooksMap as follow:
  ```
    Map<String,dynamic> hooksMap = {
      ....
      "priceFormatter" : CustomMethodsHook.getPriceFormatterHook(),
      "compactPriceFormatter" : CustomMethodsHook.getCompactPriceFormatterHook(),
    };
  ```
- If you're using older version than flutter 3.7.0, you need to lower pinput library version in `Project_HOME /packages/houzi_package/pubspec.yaml`. Set the version to 2.2.11 for the library pinput like `pinput: 2.2.11`
- Open following file:  `PROJECT_HOME/android/app/build.gradle` and look for `targetSdkVersion` and change to 31
- Open following file:  `PROJECT_HOME/android/app/src/main/AndroidManifest.xml` and look for `<Activity` tag and add an attribute `android:exported="true"`
- Delete file: `Project_HOME/l10n.yaml`
- Rest of configurations like configuration.json, you android project folders, ios project folders should remain same.

## Update from 1.1.4

> Starting 1.1.4, we adopted hooks to provide custom designs, fonts, headers and many customisation from your main project. It allows you to preserve the configs in your android and iOS app. 

Backup before doing anything with the update.

Starting with 1.1.4, all your configuration, styling and customizations are store in configurations.json that is independant of your houzi_package. With the introduction of hooks we've added the ability to provide custom designs, fonts, headers and many customisation from your main project. This helps us preserve your settings and configurations in the event of updates.

When you get the latest version source code, simply copy following folder and replace with existing folder

`Project_HOME > packages > houzi_package`

That's pretty much it. In many cases we might add new hooks for widget and customisation. Always make sure to check the original Houzi main project (not package project) code for any new hooks or configuration edition.

> **Note**: If you want to make changes to `houzi_package`, we suggest to always add comments with your identifier (your name or company name). So in the event of new updates, you can keep track of the changes you made in old houzi_package and those can be manually moved over.

## Update from 1.1.2

> Starting 1.1.2 we’ve adopted the flutter package approach to make the updates easy. Also, all your configurations are independant of the Houzi code. 

Backup before doing anything with the update.

Copy the following files into a separate folder:

`app_preferences.dart		← contains theme related configurations. `
`constants.dart			← contains app setup related configurations. `

When you get the latest version source code, simply copy following folder and replace with existing folder

`Project_HOME > packages > houzi_package`

Now replace new `app_preferences.dart` and `constants.dart` with your own files. Add any keys that are missing from the fresh copy. You can use the “compare with” tool by right clicking on existing and selecting a new file to compare with in Android Studio.

## Update from 1.1.1 and previous

Backup before doing anything with the update.

Copy the following files into a separate folder:

`app_preferences.dart		← contains theme related configurations.`
`constants.dart			← contains app setup related configurations.` 

When you get the latest version code, copy the following folder from fresh code

`Project_HOME > packages > houzi_package`

And paste it the same place in existing project (create new folder if required):

`Project_HOME > packages > houzi_package`

Now replace new `app_preferences.dart` and `constants.dart` in the `houzi_package` folder with your own files. Add any keys that are missing from the fresh copy. You can use the “compare with” tool by right clicking on existing and selecting a new file to compare with in Android Studio.


Open your existing `pubspec.yaml` and edit the dependencies to look like `pubspec.yaml` from fresh code by removing every dependency under dependencies: and adding only following:
```
dependencies:
  flutter:
    sdk: flutter

  flutter_launcher_icons: 0.9.2
  flutter_localizations:
    sdk: flutter
  houzi_package:
    path: packages/houzi_package
```

Remove everything in your `Project_HOME > lib` folder EXCEPT `main.dart`

Replace the contents of `main.dart` with this:

`import 'package:houzi_package/houzi_main.dart' as houzi_package;`
```
Future<void> main() async {
 return houzi_package.main();
}
```

Try and build the project.
