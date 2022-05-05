<!-- ---
title: Push Notification integration
category: Tools Setup
order: 14
--- -->

We’re using OneSignal for the push notification purpose. You can set up OneSignal on your wordpress and your app.

## OneSignal setup
Use the following link to sign-up/login in.

https://app.onesignal.com/login

After that follow this guide to setup the project. Keep in mind that we have installed the SDKs in the project, you just need app id so don’t follow step 3 or any further steps.
After the setup you will be provided with an app id at the end, copy that app id and go to the `Project_HOME > packages > houzi_package > lib > common > constants.dart` file, and look for `ONE_SIGNAL_APP_ID`. Replace its value with your own app id.