---
title: Setup Facebook sign in
category: Tools Setup
permalink: tools/setup_facebook_signin
order: 15
---

## Facebook sign in
For Facebook sign in, first you need to register as a Facebook developer. Follow this link:
https://developers.facebook.com/docs/development/register/

Then you have to create an app. Follow this link:
https://developers.facebook.com/docs/development/create-an-app

If you integrate Facebook login in your mobile app, Facebook cross-checks your app's ownership on your website at following address:

https://domain.com/app-ads.txt

Go to `Project_HOME  > server_files` Open and edit the app-ads.txt file and replace FB_APP_ID_GOES_HERE with your Facebook app id. And then upload to your website root folder.


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

Save changes and facebook sign in is complete.

