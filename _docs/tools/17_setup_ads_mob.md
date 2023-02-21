---
title: Google AdMob integration
category: Tools Setup
permalink: tools/setup_admob
order: 17
---

Register your app as an AdMob app by completing the following steps:
1. [Sign in](https://admob.google.com/home/) to or [Sign up](https://support.google.com/admob/answer/7356219) for an AdMob account.
2. Register your app with AdMob. This step creates an AdMob app with a unique AdMob App ID for each platform.

After getting your app AdMob App ID go to:

**Android** `houzi > android > app > src > main > res > values > strings.xml` file, and look for `google_ads_app_id`. Replace its value with your own AdMob App ID.

**iOS** `Project_HOME > ios > Runner > Info.plist` file, and look for `GADApplicationIdentifier`. Replace its value with your own AdMob App ID. 

> **Good to remember:** After creating AdMob app, update your `GoogleServices-Info.plist` for iOS and `google-services.json` for android by downloading fresh copy from firebase.

Create a native ad unit. Follow this link to get it: https://support.google.com/admob/answer/7187428#step1


## Add/Change AdMob Native ids by Houzi Config
Open houzi config and go to the section `Api & Config`. Enter your Android and iOS native ads id here

<img src="../../images/enter-ad-mob-key.JPG" alt="enter-ad-mob-key.JPG" title="enter-ad-mob-key.JPG" border= "1px solid"/>


## Add/Change AdMob Native ids by editing config.json
Copy that native ad unit and go to the `Project_HOME > assests > configuration > configuration.json` file, and look for `android_native_ad_id` for android and `ios_native_ad_id` for IOS. Replace its value with your own native ad unit.
Make sure set the value of `show_ads: true` to turn on the ads


## Add/Change AdMob Native ids by editing constants.dart
Copy that native ad unit and go to the `Project_HOME > packages > houzi_package > lib > common > constants.dart` file, and look for `ANDROID_NATIVE_AD_ID` for android and `IOS_NATIVE_AD_ID` for IOS. Replace its value with your own native ad unit.
Make sure set the value of `SHOW_ADS=true` to turn on the ads

## Enable Ad Validator to Debug your ads
AdMob sdk provides a way to validate your ads on screen. We've disabled the ad validator by default. However you can enable the ad validator to check if you've any issues with your configurations.

### Enable Ad Validator Android

Open `houzi > android > app > src > main > AndroidManifest.xml` file, and look for `com.google.android.gms.ads.flag.NATIVE_AD_DEBUGGER_ENABLED`. Replace its value `android:value="false"` to `true`.

### Enable Ad Validator iOS
Open file `Project_HOME > ios > Runner > Info.plist` file, and look for `GADNativeAdValidatorEnabled`. Replace its next tag `<false/>` with `<true/>`

This will enable ad validator for your app.