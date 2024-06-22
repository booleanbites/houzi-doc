---
title: Push Notifications
category: Tools Setup
permalink: tools/push_notifications_integration
order: 23
---

Push notifications play a crucial role in keeping your real estate business updated. We’ve incorporated this feature to enhance engagement with your app and website. 

>  **❗️❗️IMPORTANT❗️❗️**
>
>  <u>Houzez v 3.1.0</u> or later is required. This version introduces the ability to send push notifications for important actions. Please ensure you update to Houzez v 3.1.0 before implementing push notifications on your website.

We utilize OneSignal for push notifications. You will need to configure OneSignal on both your WordPress site and your app. This guide includes the following sections:

- [OneSignal setup](#onesignal-setup)
- [OneSignal setup on Wordpress](#onesignal-setup-on-wordpress)
  - [1. OneSignal App ID:](#1-onesignal-app-id)
  - [2. OneSingnal API Key Token:](#2-onesingnal-api-key-token)
  - [3. OneSingnal User Key Token:](#3-onesingnal-user-key-token)
- [OneSignal setup on App](#onesignal-setup-on-app)
  - [1. Android native project:](#1-android-native-project)
  - [2. iOS native project:](#2-ios-native-project)
  - [3. Houzi Package via Houzi Builder](#3-houzi-package-via-houzi-builder)



## OneSignal setup

We require three things from OneSignal.
1. OneSignal App ID
2. OneSingnal API Key Token
3. OneSingnal User Key Token

To acquire these, use the following link to sign-up/login in. `https://app.onesignal.com/login`

A typical flow should like this:

1. You use social login or signup with email & password.
   - You will be asked to choose the plan. Choose Free plan and Click on Get Started Now.
2. Provide your info in About You section. Choose "Drive Visits to Website/App" and Choose "Push Notification" for channel options.
3. Provide info about your organization.
4. Provide info about your app.
5. In the following Welcome page, choose below options
   1. Messaging Channels -> Push Notifications.
   2. **Android:**
      1. Choose Android. and continue, you will be asked to upload your firebase configruation file. Follow the guide by OneSignal. [Android Guide](https://documentation.onesignal.com/docs/android-firebase-credentials) to get the firebase configruation file.
      2. Once firebase-adminsdk-key is uploaded, You can choose Flutter in next step. Click save and Continue.
      3. Copy the app id and click done.
   3. **iOS**
      1. From the Inactive platforms, choose iOS. You need paid Apple Developer Membership program for this step.
      2. You will be asked to provide APNs info. Follow the guide by OneSignal for acquiring the p8 file from AppleDeveloper portal. [iOS Guide](https://documentation.onesignal.com/docs/ios-p8-token-based-connection-to-apns)
      3. Once .p8 key file is uploaded, You can enter the other info and Save And Continue. You can choose Flutter in next step. Click save and Continue.
      4. Copy the app id and click done. Both app id should be same.

> Keep in mind that we already have integrated the SDKs in the project, you just need app id so don’t follow steps to integrate sdks.

## OneSignal setup on Wordpress

Go to the `Houzi Api > Push Notification > OneSignal Configurations`.

<img src="../../images/one-signal-wordpress-config.png" alt="one-signal-wordpress-config" title="one-signal-wordpress-config" border="1px solid"/>  

You have to provide these following configurations:

### 1. OneSignal App ID:

Provide your *OneSignal App ID* in the respective text field.<br/>If you do not know how to get the *One Signal App ID*, Go to https://app.onesignal.com/apps/ page, find your application, and open it. You can find the APP ID in the URL.
Or go to **Settings** tab and find in **Keys and Ids** section of settings.

### 2. OneSingnal API Key Token:

Provide your *OneSingnal API Key Token* in the respective text field. If you do not know how to get the *OneSingnal API Key Token*, Go to https://app.onesignal.com/apps/YOUR_APP_ID/settings/keys_and_ids page.

> If you don't have a Rest API Key already generated, please generate a new one by clicking the **Generate New API Key** button.


### 3. OneSingnal User Key Token:

Provide your *OneSingnal User Key Token* in the respective text field. If you do not know how to get the *OneSingnal User Key Token*, Go to https://app.onesignal.com/profile page and scroll down to the **User Auth Key** section.

> If you don't have a key already generated, please generate a new one by clicking the **Generate New User Auth Key** button.


After providing the configurations, click on the **Save Changes** button.


## OneSignal setup on App

Copy your *OneSignal App ID*. If you do not know how to get the *One Signal App ID*, Go to https://app.onesignal.com/apps/ page, find your application, and open it. You can find the APP ID in the URL.
Or go to **Settings** tab and find in **Keys and Ids** section of settings.

You will have to provide this app id in the following destinations (Mandatory):

### 1. Android native project:
Nees to setup two things:
1. Open AndroidManifest.xml and Find meta tag and change its value to your own package for NotificationServiceExtension, if you haven't done already. Follow guide here: [OneSignal Push Configurations for Android](../app-setup/change_app_identifier#onesignal-push-configurations-for-android)
2. Go to the `Project_HOME > android > app > src > main > res > values > strings.xml` file, and look for `onesignal_app_id`. Replace its value with your app id.

### 2. iOS native project:
Nees to setup two things:
1. Setup App group bundle identfier for App Groups for NotificationServiceExtension, if you haven't done already. App Group identifier help share resources between app and NotificationServiceExtension. Follow guide here: [OneSignal Push Configurations for iOS](../app-setup/change_app_identifier#onesignal-push-configurations-for-ios)
2. Go to the `Project_HOME > ios > Runner > AppDelegate.swift` file, and look for `ONE_SIGNAL_APP_ID`. Replace its value with your app id.

### 3. Houzi Package via Houzi Builder

Go to the **Api & Config** section of  the Houzi Builder and provide the *OneSignal App ID* in the respective text field. Checkout HouziBuilder [Push Notifications Configurations](/houzi-builder/api_config_setup#push-notification-configurations).   

If you don't want to use HouziBuilder, open configuration.json and find `one_signal_app_id` and provide your OneSignal App ID as its value. If the key doesn't exist in your configuration, you can add as a new key in the root object of json.

 *Added in version 1.4.0*