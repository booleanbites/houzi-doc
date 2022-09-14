---
title: Setup DeepLink
category: Tools Setup
order: 18
---


 To setup DeepLink in app for `Android` go to `houzi > android > app > src > main > res > values > strings.xml` file, look for `scheme`,`host` and `path_prefix`. Replace its value with your own scheme (http or https) and domain host.

 To setup DeepLink in app for `iOS` go to `houzi > iOS > Runner > Info.plist` file, look for key `CFBundleURLName`, replace it with your host and `CFBundleURLSchemes` replace it with your host.


## These two files are related to deep links:

1. apple-app-site-association
2. assetlinks.json

You need to upload these files to your website root folder / .well-known directory and they must be publicly accessible like below:

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