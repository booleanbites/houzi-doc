---
title: Setup Firebase
category: Tools Setup
permalink: tools/firebase_setup
order: 7
---

> Make sure your desired app bundle identifiers are set before setting up firebase.


Firebase is necessary to be set up if you want analytics, planning to support push notifications and other diagnostic related data.

### Android setup (mandatory)
https://firebase.google.com/docs/android/setup

### iOS setup (mandatory)
https://firebase.google.com/docs/ios/setup

### App setup (mandatory)

After acquiring the **json** and **plist** for both platforms. Place them at following places:

- Android: `Project_HOME > android > app > google-services.json`

- iOS: `Project_HOME > ios > Runner > GoogleServices-Info.plist`