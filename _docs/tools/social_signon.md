---
title: Setup Social Sign On
category: Tools
order: 15
---

Houzi supports social sign ons. Android app offers Google and Facebook SSO, and iPhone app offer SSO with Apple, Google and Facebook.

> **Note**: If your iOS app offers social login with either facebook or Google, Apple login is a must in order to get the iOS app approved from Apple, its required to support Sign in with Apple, you cannot disable it on iPhone app and keep facebook or Google.

## Google Sign On
The keystore that you intend to use to sign the Android app will be used in this step. YOu might have already created this keystore in previous sections. After generating a signing key, the next step is to add SHA-1 and SHA-256 certificates to the firebase project. You go to the `Firebase console > project > project settings > Add fingerprint`
Here you add your SHA-1 and SHA-256 certificates, that you generated from your signing key and from the Google play console.

To generate SHA-1 and SHA-256 certificates from the key:
https://developers.google.com/android/guides/client-auth#using_keytool_on_the_certificate

To get SHA-1 and SHA-256 certificates from the Google play console:
https://developers.google.com/android/guides/client-auth#using_play_app_signing

After adding the certificates, download the `google-services.json`. Place it at following place:

- Android: `Project_HOME > android > app > google-services.json`

Also download the `GoogleServices-Info.plist` for iOS and place it here:

- iOS: `Project_HOME > ios > Runner > GoogleServices-Info.plist`

For iOS you need to provide a URL scheme for Google Sign On, open the `GoogleService-Info.plist` configuration file, and look for the `REVERSED_CLIENT_ID` key. Copy the value of that key, and paste it into the URL Schemes box on the configuration page

`Project_HOME > ios > Runner > Info Tab > URL Types section > Google Login Scheme`


On completing above mentioned steps, google sign on is functional.(No additional work is required).

You might need to copy your PlayStore sha1 in your firebase as well to get the google login working.

### Apple Sign On
Integrate Apple Sign on by following:
[sign_in_with_apple | Flutter Package (pub.dev)](https://pub.dev/packages/sign_in_with_apple#integration)

You can skip the Android and Web sections.

After integrating, go to `Project_HOME > packages > houzi_package > lib > common > constants.dart` and look for `APPLE_SIGN_ON_CLIENT_ID` add `APPLE_SIGN_ON_REDIRECT_URI`. Replace their values with your own Service ID and Redirect Uri.

### Facebook Sign On
For Facebook signOn, first you need to register as a Facebook developer. Follow this link:
https://developers.facebook.com/docs/development/register/

Then you have to create an app. Follow this link:
https://developers.facebook.com/docs/development/create-an-app


#### Android
After creating app you will refer to app dashboard, on the top left your app id is mentioned, copy the app id and go to strings.xml file

`Project_HOME > android > app > src > main > res > values > strings.xml` and look for `facebook_app_id`. Replace its value with your own app id.

On facebook dashboard, go to Settings > Advanced and look for client token, copy it and go to strings.xml file and paste it for `facebook_client_token`.

On facebook dashboard, go to `Settings > Basic` fill your basic information and at the end of the page click on Add platform. Select android and then Google Play Store. Then go to `Project_HOME > android > app > src > main >  AndroidManifest.xml` copy your package name and paste it in the Package Names field. Then copy the package name and paste in Class Name and write .MainActivity with your package name like this YOURPACKAGENAME.MainActivity 
(e.g com.houzi.app.MainActivity).

Then put your hashkey in the Key hashes field. To find info to how to generate you key hash go to  
https://developers.facebook.com/docs/facebook-login/android?locale=en_US#6--provide-the-development-and-release-key-hashes-for-your-app

**OR** to quickly find your hash key, copy your SHA-1 certificate and go to this website http://tomeko.net/online_tools/hex_to_base64.php paste it in the hex string field and you will get your key hashes in the output field.


#### IOS
On facebook dashboard, go to `Settings > Basic` at the end of the page click on Add platform and fill in the details.

Open `Project_HOME > ios > Runner > Info >`

`FacebookAppID, FacebookClientToken, FacebookDisplayName`

Replace these with your own facebook app id, client token and your app name.

Also look for the Facebook Login Scheme in the URL types `(CFBundleURLTypes)` section and enter your own facebook app id with fb prefixed like this:

fb1122334455667788

Save changes and facebook Sign on is complete.

