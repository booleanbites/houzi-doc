---
title: Change Website URL
category: App Setup
order: 1
---

open the `houzi > packages > houzi_package > lib > common > constants.dart` file, and look for `WORDPRESS_URL_DOMAIN` and `WORDPESS_URL_SCHEME`. Replace with your own domain and scheme.

```
//Mandatory
String WORDPRESS_URL_DOMAIN = "domain.com";
String WORDPRESS_URL_SCHEME = "https";
const String WORDPRESS_URL_PATH = "";
```

if your website URL does not contain a subpath then leave `WORDPRESS_URL_PATH` as it is.

You nedd to provide following URL to your website pages

```
//Optional
const String APP_TERMS_URL = "https://domain.com/terms.html";
const String APP_PRIVACY_URL = "https://domain.com/privacy.html";
const String APP_TERMS_OF_USE_URL = "https://domain.com/terms.html";
const String WORDPRESS_URL_GDPR_AGREEMENT = "https://domain.com/gdpr.html";

/// Your Company Related
String COMPANY_NAME = "BooleanBites Ltd.";
String COMPANY_URL = "https://booleanbites.com";
```

> **Important**: If you are using non secure domain, add your domain to following files for mobile systems to allow communication to non-secure domain: 

- Android: `network_security_config.xml`
- iOS: `NSAppTransportSecurity` key in `info.plist`

Read guides here:

- Android: https://developer.android.com/training/articles/security-config
- iOS: https://developer.apple.com/documentation/bundleresources/information_property_list/nsapptransportsecurity


