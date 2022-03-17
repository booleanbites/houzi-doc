---
title: Changing Splash screen
category: App Setup
order: 4
---

**Flutter command:** You can change splash background by adding this flutter library: 
https://pub.dev/packages/flutter_native_splash
Follow instructions for changing splash from one place.

## Manual method
You can manually change splash screen in Android and iOS projects at following places:

#### Android: `Project_HOME > android > app > src > main > res > values > strings.xml`

##### Background Color
Change the "backgroundColor" with hex color like this:
```
<color name="backgroundColor">#2B3D2D</color>
```
##### Splash icon
To change or remove the splash icon, open these files:

- Lite: `Project_HOME > android > app > src > main > res > drawable > launch_background.xml`
- Dark: `Project_HOME > android > app > src > main > res > drawable-night > launch_background.xml`

To remove the icon, remove these line:
```
<item>
    <bitmap
        android:gravity="center"
        android:src="@drawable/ic_launcher" />
</item>
```
To edit or replace the icon, replace the image file at this place:

- Lite: `Project_HOME > android > app > src > main > res > drawable > ic_launcher.png`
- Dark: `Project_HOME > android > app > src > main > res > drawable-night > ic_launcher.png`

The icon can be of any size. You can use any name with icon file, just update the reference in `launch_background.xml`


### iOS
`Project_HOME > ios > Runner > Runner > LaunchScreen`
Open LaunchScreen and it’ll show you a graphical interface to edit your launch screen. You can add text, photos and anything on your screen. To learn more, read the official docs here: [Specifying Your App’s Launch Screen](https://developer.apple.com/documentation/xcode/specifying-your-apps-launch-screen/)

#### Run App
Once everything is set up. Do a flutter clean, so flutter picks up the new configuration and setup everything in child projects.
From top menu toolbar select `Tools > Flutter > Flutter Clean`
From top menu toolbar select `Run > Run main.dart`

Wait… and see if it compiles and run for you.
