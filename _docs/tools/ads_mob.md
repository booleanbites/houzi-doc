---
title: Google AdMob integration
category: Tools Setup
order: 16
---

Register your app as an AdMob app by completing the following steps:
[Sign in](https://admob.google.com/home/) to or [sign up](https://support.google.com/admob/answer/7356219) for an AdMob account.
Register your app with AdMob. This step creates an AdMob app with a unique AdMob App ID for each platform.

After getting your app AdMob App ID go to:

**Android** `houzi > android > app > src > main > res > values > strings.xml` file, and look for `google_ads_app_id`. Replace its value with your own AdMob App ID.

**iOS** `Project_HOME > ios > Runner > GoogleServices-Info.plist` file, and look for `ADMOB_APP_ID`. Replace its value with your own AdMob App ID. Although its automatically linked from your firebase settings, but its good to have a look at it.

Create a native ad unit. Follow this link to get it: https://support.google.com/admob/answer/7187428#step1

Copy that native ad unit and go to the `houzi > packages > houzi_package > lib > common > constants.dart` file, and look for `ANDROID_NATIVE_AD_ID` for android and `IOS_NATIVE_AD_ID` for IOS. Replace its value with your own native ad unit.
Make sure set the value of `SHOW_ADS=true` to turn on the ads