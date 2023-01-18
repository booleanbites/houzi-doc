---
title: Setup Apple social sign in
category: Tools Setup
permalink: tools/setup_apple_signin
order: 17
---

> **Note**: If your iOS app offers social login with either facebook or Google, Apple login is a must in order to get the iOS app approved from Apple, its required to support Sign in with Apple, you cannot disable it on iPhone app and keep facebook or Google.


## Apple sign in
Integrate Apple sign in by following:
[sign_in_with_apple | Flutter Package (pub.dev)](https://pub.dev/packages/sign_in_with_apple#integration)

You can skip the Android and Web sections.

If you want to enable Android, then follow the steps in library guide and then go to `Project_HOME > packages > houzi_package > lib > common > constants.dart` and look for `APPLE_SIGN_ON_CLIENT_ID` add `APPLE_SIGN_ON_REDIRECT_URI`. Replace their values with your own Service ID and Redirect Uri. 

> These constants not needed if you just want to enable Apple sign in for iOS only.



