---
title: Setup Firebase
category: Tools
order: 6
---

> Make sure your desired app bundle identifiers are set before setting up firebase.


Firebase is necessary to be set up if you want analytics, planning to support push notifications and other diagnostic related data.

### Android setup (mandatory)
https://firebase.google.com/docs/android/setup
### iOS setup (mandatory)
https://firebase.google.com/docs/ios/setup

After acquiring the json and plists for both platforms. Place them at following places:

#### Android: 
Project_HOME > android > app > google-services.json

#### iOS: 
Project_HOME > ios > Runner > GoogleServices-Info.plist