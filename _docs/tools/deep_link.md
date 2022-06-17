---
title: Setup DeepLink
category: Tools Setup
order: 18
---

## Android:

 To setup DeepLink in app for Android go to `houzi > android > app > src > main > res > values > strings.xml` file, look for `scheme`,`host` and `path_prefix`. Replace its value with your own scheme (http or https) and domain host.

To verify ownership of both your app and your website:
Go to `Android Studio > Tool > AppLinksAssistance > Associate Website` Fill the form and download the assetlink.json



## iOS:

 To setup DeepLink in app for iOS go to `houzi > iOS > Runner > Info.plist` file, look for key `CFBundleURLName`, replace it with your host and `CFBundleURLSchemes` replace it with your host.