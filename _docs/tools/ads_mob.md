---
title: Google AdMob integration
category: Tools
order: 16
---

Register your app as an AdMob app by completing the following steps:
[Sign in](https://admob.google.com/home/) to or [sign up](https://support.google.com/admob/answer/7356219) for an AdMob account.
Register your app with AdMob. This step creates an AdMob app with a unique AdMob App ID.

After getting your app AdMob App ID go to `houzi > android > app > src > main > res > values > strings.xml` file, and look for `google_ads_app_id`. Replace its value with your own AdMob App ID.

Create a native ad unit. Follow this link to get it: https://support.google.com/admob/answer/7187428#step1

Copy that native ad unit and go to the `houzi > packages > houzi_package > lib > common > constants.dart` file, and look for `ANDROID_NATIVE_AD_ID` for android and `IOS_NATIVE_AD_ID` for IOS. Replace its value with your own native ad unit.
Make sure set the value of `SHOW_ADS=true` to turn on the ads