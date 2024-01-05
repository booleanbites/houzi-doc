---
title: Setup Google social sign in
category: Tools Setup
permalink: tools/setup_google_signin
order: 15
---

## Google sign in
The keystore that you intend to use to sign the Android app will be used in this step. YOu might have already created this keystore in previous sections. After generating a signing key, the next step is to add SHA-1 and SHA-256 certificates to the firebase project. You go to the `Firebase console > project > project settings > Add fingerprint`
Here you add your SHA-1 and SHA-256 certificates, that you generated from your signing key and from the Google play console.

To generate SHA-1 and SHA-256 certificates from the key:
https://developers.google.com/android/guides/client-auth#using_keytool_on_the_certificate

To get SHA-1 and SHA-256 certificates from the Google play console:
https://developers.google.com/android/guides/client-auth#using_play_app_signing


> You might also want to set the project name and email in Firebase > Settings > General > Public settings 

### Enable Google Sign-In for your Firebase project

To allow users to sign in using Google Sign-In, you must first enable the Google Sign-In provider for your Firebase project:

1. In the Firebase console, open the Authentication section.
2. On the Sign in method tab, enable the Google provider.
3. Click Save.

After adding the certificates, download the `google-services.json`. Place it at following place:

- Android: `Project_HOME > android > app > google-services.json`

Also download the `GoogleServices-Info.plist` for iOS and place it here:

- iOS: `Project_HOME > ios > Runner > GoogleServices-Info.plist`

For iOS you need to provide a URL scheme for Google sign in, open the `GoogleService-Info.plist` configuration file, and look for the `REVERSED_CLIENT_ID` key. Copy the value of that key, and paste it into the URL Schemes box on the configuration page

`Project_HOME > ios > Runner > Info Tab > URL Types section > Google Login Scheme`


On completing above mentioned steps, google sign in is functional.(No additional work is required).

You might need to copy your PlayStore sha1 in your firebase as well to get the google login working.



