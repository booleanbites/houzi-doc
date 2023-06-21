---
title: Welcome
---

![Houzi real estate](images/banner.jpg)

Houzi a real estate mobile application for real estate agents and agencies. Its build with Flutter so it can be deployed to Android and iOS.

### Pathway

We've compiled a list of the most required things that you need to do in order to launch the app on device. We assume you have a website setup with Houzez. We also assume that you've purchased [Houzi app from CodeCanyon](https://codecanyon.net/item/houzi-real-estate-app/39753350).

1. [Setup Houzi plugin](tools/houzi_plugin)
2. [Setup App Secret](tools/app_secret)
3. [Setup JWT Auth plugin](tools/jwt_auth_plugin_setup)
4. [Install and setup Android Studio](tools/android_setup)
5. [Install and setup Flutter](tools/flutter_setup)
6. [Install and setup Xcode](tools/xcode_setup) (Optional)
7. [Tell your app about your website address](app-setup/change_app_url)
8. Launch on device

At this point, the app will still show Houzi branding, but it'll show your website data. Now to do the branding, you'll need to do following things:

1. Change [App Identifier](app-setup/change_app_identifier) AND [App name](app-setup/change_app_display_name) AND [App Icon](app-setup/change_app_icon) AND [Splash screen](app-setup/change_app_splash_screen)
2. [Create your own keystore](tools/setup_android_signing)
3. [Setup firebase](tools/firebase_setup)
4. [Setup GoogleCloud](tools/google_cloud_setup)
5. [Change App Theme](app-setup/change_app_theme)
6. Launch on device

At this point, the app will show your branding, with your data with firebase and google cloud project integrated. Go ahead and configure following things:

1. Configure Social Logins [Google](tools/setup_google_signin), [Facebook](tools/setup_facebook_signin), [Apple](tools/setup_apple_signin)
2. Configure [Phone Login](tools/setup_phone_signin)
3. Do any customization from [Houzi Builder](houzi-builder/intro) or [Hooks & Widgets](hooks-widgets/add_item_in_drawer).
4. Launch on device.


### Documentation

#### [Tools](tools/tools_setup)

This section addresses all the tools and other environment configurations you need to do get the development started.

#### [App Setup](app-setup/change_app_url)

This section guides through all the steps related to app setup and customization.

#### [Hooks & Widgets](hooks-widgets/add_item_in_drawer)

We have designed many hooks to provide way of customizing styles, designs and provide additional info to the app.

#### [Houzi Config Builder](houzi-builder/intro)

Houzi Builder is a desktop visual config builder. This section talks about designing and generating configuration with Houzi Builder, that can be used in the app.

### Try the demo app here:

 [![Houzi real estate](images/apple_store.png)](https://apps.apple.com/us/app/id1598357211)  [![Houzi real estate](images/google_play.png)](https://play.google.com/store/apps/details?id=com.booleanbites.houzez)

 