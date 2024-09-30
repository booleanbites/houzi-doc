---
title: Setup Google Cloud
category: Tools Setup
permalink: tools/google_cloud_setup
order: 7
---


<br/>
<iframe width="560" height="315" src="https://www.youtube.com/embed/zTwFI-cPgtk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br/>
<br/>


When you create a Firebase project, a corresponding Google Cloud project is automatically created. This Google Cloud project serves as the underlying infrastructure for your Firebase project, allowing you to use various Google Cloud services (such as Maps, Places Api, Play Integrity, etc.) in conjunction with Firebase.

Headover to Google [Google Cloud Console](https://console.cloud.google.com/). Click the Project dropdown in the top-left corner.
**Select your project** from the list or search for it. Then enable following options.

- [Enable Maps Api](https://developers.google.com/maps/documentation/android-sdk/start#enable-api-sdk).
- [Enable Places Api](https://developers.google.com/maps/documentation/places/android-sdk/cloud-setup).
- [Enable Static Maps Api](https://developers.google.com/maps/documentation/maps-static/cloud-setup).
- [Acquire Maps Api Key](https://developers.google.com/maps/documentation/android-sdk/start#get-key).
- [Enable Google Play Integrity API](https://developer.android.com/google/play/integrity/setup) - Navigate to APIs and services. Select enable APIs and services. Search for Play Integrity API and then enable it.

Once done, it is always a good idea to download latest configuration file from firebase console and update them at following place:

- Android: `Project_HOME > android > app > google-services.json`
- iOS: `Project_HOME > ios > Runner > GoogleServices-Info.plist`