---
title: Setup Phone sign in
category: Tools Setup
permalink: tools/setup_phone_signin
order: 16
---

The phone signup feature allows users to register for the mobile app using their phone numbers. Users will receive a verification code via SMS, which they must enter to complete the registration process. We have integrated firebase phone signup feature in the app. Make sure you have done following things before continuing:

1. [Changed App Identifier](../app-setup/change_app_identifier) 
2. Have setup [Custom Keystore](../tools/setup_android_signing)
3. [Firebase integrated](../tools/tools/firebase_setup)
4. [GoogleCloud integrated](../tools/google_cloud_setup)
5. Attached a payment method to your GoogleCloud.
   
> Important: Adding a payment method to your Google Cloud Project is necessary for firebase to send an sms. Firebase allows **10 Free SMS per day**. But it requires you to have payment method added.


The keystore that you intend to use to sign the Android app will be used in this step. You might have already created this keystore in previous sections. After generating a signing key, the next step is to add SHA-1 and SHA-256 certificates to the firebase project. You go to the `Firebase console > project > project settings > Add fingerprint`
Here you add your SHA-1 and SHA-256 certificates, that you generated from your signing key and from the Google play console.

To generate SHA-1 and SHA-256 certificates from the key:
https://developers.google.com/android/guides/client-auth#using_keytool_on_the_certificate

To get SHA-1 and SHA-256 certificates from the Google play console:
https://developers.google.com/android/guides/client-auth#using_play_app_signing


> You might also want to set the project name and email in Firebase > Settings > General > Public settings 

After adding the certificates, download the `google-services.json`. Place it at following place:

- Android: `Project_HOME > android > app > google-services.json`

Also download the `GoogleServices-Info.plist` for iOS and place it here:

- iOS: `Project_HOME > ios > Runner > GoogleServices-Info.plist`

For iOS you need to provide a URL scheme for Google sign in, open the `GoogleService-Info.plist` configuration file, and look for the `REVERSED_CLIENT_ID` key. Copy the value of that key, and paste it into the URL Schemes box on the configuration page

`Project_HOME > ios > Runner > Info Tab > URL Types section > Google Login Scheme`

Now with Phone Sign In setup, ensure you have followed these steps:

#### Step 1
Enable Phone as a Sign-In method in the Firebase console. Go to `Firebase console > Authentication > Enable Phone` 


#### Step 2
Goto Firebase > Project Settings > Your Apps > Android app. Make sure to add SHA-1 and SHA-256 fingerprints under SHA certificate fingerprints.

#### Step 3
Goto Firebase > [App Check](https://console.firebase.google.com/project/_/appcheck) > Apps. And Register your app for **Play Integrity**. Read here about [App Check Documentation](https://firebase.google.com/docs/app-check/flutter/default-providers)

#### Step 4
Go to Google Cloud, APIs & Services section and enable `Google Play Integrity API`

After these step you are good to go sign in with Phone



