---
title: Setup Phone sign In
category: Tools Setup
order: 18
---

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
Make sure to add SHA-1 and SHA-256 certificates to the firebase project


#### Step 3
Go to Google cloud and enable `Android Device Verification`

After these step you are good to go sign in with Phone



