---
title: Setup Deep Link
category: Tools Setup
order: 19
---

Deep links or Universal link is the ability of your application being launch after user open website url and you want to open the URL in the application. We have added the ability to open property profile, when a property URL is opened on mobile.

> **Note**: Right now application consider permalinks when it finds patterns as domain.com/property/, so make sure you are using this format in your website settings. Otherwise you can make changes to the URL supported in Android and iOS code.

## Setup Application:
### Android:
 To setup Deep Link in app, go to `Project_HOME > android > app > src > main > res > values > strings.xml` file, look for `scheme`,`host` and `path_prefix`. Replace its value with your own scheme (http or https) and domain host.
### iOS:
 To setup Deep Link in app for iOS go to `Project_HOME > iOS > Runner > Info.plist` file, look for key `CFBundleURLName`, replace it with your host and `CFBundleURLSchemes` replace it with your scheme. Example below:
```
<key>CFBundleURLTypes</key>
<array>
    ....
    <dict>
        <key>CFBundleTypeRole</key>
        <string>Editor</string>
        <key>CFBundleURLName</key>
        <string>your_good_domain_here.com</string>
        <key>CFBundleURLSchemes</key>
        <array>
            <string>https</string>
        </array>
    </dict>
    ....
</array>
```

## Setup Server File:

1. apple-app-site-association
2. assetlinks.json

These files are located in your source code `Project_HOME  > server_files`. You need to upload these files to your website root folder / .well-known directory and they must be publicly accessible like below:

https://domain.com/.well-known/apple-app-site-association
https://domain.com/.well-known/assetlinks.json

#### Android Asset Links:

Go to `Project_HOME  > server_files` Open and Edit `assetlinks.json` file and enter your app package name against `package_name` key like below:

```
"package_name": "com.domain.app"
```
You also need to provide sha256 of your keystore.

There're two flavour of same app in this files. One is for production sha256 and the other is for development purpose.

#### Apple App Site Association:

Go to `Project_HOME  > server_files` Open and edit the `apple-app-site-association` file and enter your apple developer team id and app identifier against `appID` key like below:

```
"appID": "TEAM_ID_XX.com.domain.app"
```

That's pretty much it, now your application should open the URL.

> **Note**: You might need to restart the device or wait for few hours in case it is not working.