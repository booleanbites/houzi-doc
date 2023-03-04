---
title: Setup App Secret
category: Tools Setup
permalink: tools/app_secret
order: 2
---

Security is really importan, so we need to make communication between app and website secure. App Secret is a secret key that is used by your app when communicating with Wordpress and Rest Api.

> **Important** You need to activate your rest api plugin and also unlock it with your purchase code. Otherwise you won't be able to setup Secret Key and many other configurations.

### Setup a secret key on Admin Panel
You can enter any string of 10 to 20 characters lenght. (shouldn't be too long, though). When saved, Rest Api running on your website would look for app secret when any important communication is done, like add new property, user login, sign up or send email etc.

### Setup a secret key on mobile app
How your app will send secret key? The app needs to send this secret key in [header hook](/hooks-widgets/set_api_header). Read instruction below:

open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getHeaderMap()` method. and find key value pair for 'app-secret' in a given map. eg: 
```
  …
    Map<String, dynamic> map = {
      ...
      "app-secret": "!296@#%234^&*()_-+=", 
    };
  …
```

Make sure both keys on mobile app and website should be same, and keep them safe.



