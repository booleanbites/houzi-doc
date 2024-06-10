---
title: Push Notifications integration
category: Tools Setup
permalink: tools/push_notifications_integration
order: 24
---

We’re using OneSignal for the push notification purpose. You can set up OneSignal on your wordpress and your app. This guide consists of following sections:

1. [OneSignal setup](#onesignal-setup)  
2. [OneSignal setup on Wordpress](#onesignal-setup-on-wordpress)
3. [OneSignal setup on App](#onesignal-setup-on-app)  
4. [OneSignal setup on Houzi Builder](#onesignal-setup-on-houzi-builder)

## OneSignal setup

Use the following link to sign-up/login in.

https://app.onesignal.com/login

After that follow this guide to setup the project. Keep in mind that we have installed the SDKs in the project, you just need app id so don’t follow step 3 or any further steps.

## OneSignal setup on Wordpress

Go to the `Houzi Api > Push Notification > OneSignal Configurations`.

<img src="../../images/one-signal-wordpress-config.png" alt="one-signal-wordpress-config" title="one-signal-wordpress-config" border="1px solid"/>  

You have to provide these following configurations:

### 1. OneSignal App ID:

Provide your *OneSignal App ID* in the respective text field. If you do not know how to get the *One Signal App ID*, Go to https://app.onesignal.com/apps/ page, find your application, and open it. You can find the APP ID in the URL.
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

You will have to provide this app id in the following destinations:

### 1. Houzi Package:

Go to the `Project_HOME > packages > houzi_package > lib > common > constants.dart` file, and look for `ONE_SIGNAL_APP_ID`. Replace its value with your app id.

### 2. Android Directory:

Go to the `Project_HOME > android > app > src > main > res > values > strings.xml` file, and look for `onesignal_app_id`. Replace its value with your app id.

### 3. iOS Directory:

 and go to the `Project_HOME > ios > Runner > AppDelegate.swift` file, and look for `ONE_SIGNAL_APP_ID`. Replace its value with your app id.


 ## OneSignal setup on Houzi Builder

 Go to the **Api & Config** section of  the Houzi Builder and provide the One *Signal App ID* in the respective text field. 
 
For further assiatance [Push Notifications Configurations](/houzi-builder/api_config_setup#push-notification-configurations).   