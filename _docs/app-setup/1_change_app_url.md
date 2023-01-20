---
title: Change Website URL
category: App Setup
permalink: app-setup/change_app_url
order: 201
---

## Change URL by Houzi Config
 You can use Houzi Config Builder to [Change Website URL](/houzi-builder/basic_setup) and provide many other URLs required for the app. 


## Change URL by editing config.json
Open the `Project_HOME > assests > configuration > configuration.json` file, and look for `wordpress_url_domain` and `wordpress_url_scheme`. Replace with your own domain and scheme.

```
//Mandatory
"wordpress_url_scheme": "https",
"wordpress_url_domain": "domain.com",
"wordpress_url_path": "",
```
if your website URL does not contain a subpath then leave `wordpress_url_path` as it is.

You need to provide following URL to your website pages

```
//Optional
"app_terms_url": "https://domain.com/terms.html",
"app_privacy_url": "https://domain.com/privacy.html",
"app_terms_of_use_url": "https://domain.com/terms.html",
"wordpress_url_gdpr_agreement": "https://domain.com/gdpr.html",

/// Your Company Related
"company_url": "https://booleanbites.com",

```

<!-- 
## Change URL by editing constants.dart
Although not advised, as these will be overriden by config.json, you can hardcode the URLs in constants.dart. Open the `Project_HOME > packages > houzi_package > lib > common > constants.dart` file, and look for `WORDPRESS_URL_DOMAIN` and `WORDPESS_URL_SCHEME`. Replace with your own domain and scheme.

```
//Mandatory
String WORDPRESS_URL_DOMAIN = "domain.com";
String WORDPRESS_URL_SCHEME = "https";
const String WORDPRESS_URL_PATH = "";
```

if your website URL does not contain a subpath then leave `WORDPRESS_URL_PATH` as it is.

You need to provide following URL to your website pages

```
//Optional
const String APP_TERMS_URL = "https://domain.com/terms.html";
const String APP_PRIVACY_URL = "https://domain.com/privacy.html";
const String APP_TERMS_OF_USE_URL = "https://domain.com/terms.html";
const String WORDPRESS_URL_GDPR_AGREEMENT = "https://domain.com/gdpr.html";

/// Your Company Related
String COMPANY_NAME = "BooleanBites Ltd.";
String COMPANY_URL = "https://booleanbites.com";
``` -->

> **Important**: If you are using non secure domain, add your domain to following files for mobile systems to allow communication to non-secure domain: 

- Android: `network_security_config.xml`
- iOS: `NSAppTransportSecurity` key in `info.plist`

Read guides here:

- Android: [Network security configuration](https://developer.android.com/training/articles/security-config)
- iOS: [NSAppTransportSecurity](https://developer.apple.com/documentation/bundleresources/information_property_list/nsapptransportsecurity)


