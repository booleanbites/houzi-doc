---
title: Changing App Icon
category: App Setup
order: 3
---

**Flutter Launcher Icons** has been designed to help quickly generate launcher icons for both Android and iOS: 
1. [Flutter Launcher Icon](https://pub.dartlang.org/packages/flutter_launcher_icons).

2. Add the package to your `pubspec.yaml` file (within your Flutter project) to use it.
```
dev_dependencies:
  flutter_launcher_icons: "0.9.2"
```
3. Within the `pubspec.yaml` file specify the path of the icon you wish to use for the app and then choose whether you want to use the icon for the iOS app, Android app or both.
```
flutter_icons:
  android: true
  ios: true
  image_path: "assets/icon/icon.png"
```

4. After setting up the configuration, all that is left to do is run the package.
```
flutter pub get
flutter pub run flutter_launcher_icons:main
```

The default launcher icons have now been replaced with your custom icon.

#### Manual method
You can manually replace icons in Android and iOS projects at following places:

- Android: `Project_HOME > android > app > src > main > res > drawable`
- iOS: `Project_HOME > ios > Runner > Assets.xcassets`

Keep in mind, in a manual method, you’ll have to generate icons in different resolutions. There’s plenty of tools available that can take your high-res icon and convert them to platform supported resolutions.
