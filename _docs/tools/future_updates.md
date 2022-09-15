---
title: Upgrading with future updates
category: Tools Setup
order: 17
---

Always make a backup before updating to the next version. Starting 1.1.4 we’ve adopted the flutter package approach to make the updates easy. Also, all your configurations are independant of the Houzi code. It allows you to preserve the configs in your android and iOS app.

## Update from 1.1.4
Backup before doing anything with the update.

Starting with 1.1.4, all your configuration, styling and customizations are store in configurations.json that is independant of your houzi_package. With the introduction of hooks we've added the ability to provide custom designs, fonts, headers and many customisation from your main project. This helps us preserve your settings and configurations in the event of updates.

When you get the latest version source code, simply copy following folder and replace with existing folder

`Project_HOME > packages > houzi_package`

That's pretty much it. In many cases we might add new hooks for widget and customisation. Always make sure to check the original Houzi main project (not package project) code for any new hooks or configuration edition.

> **Note**: If you want to make changes to `houzi_package`, we suggest to always add comments with your identifier (your name or company name). So in the event of new updates, you can keep track of the changes you made in old houzi_package and those can be manually moved over.

## Update from 1.1.2 or 1.1.3
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
