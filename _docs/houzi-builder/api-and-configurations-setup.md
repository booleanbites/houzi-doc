---
title: Api and Configurations Setup
category: Houzi Builder
order: 25
---

> **Important**: You are required to install the Houzi Plug-in on your Houzez wordpress. To install the Plug-in, click on [Houzi Plug-in Link](https://github.com/AdilSoomro/houzez-mobile-api).

You can provide information regarding different **APIs** (e.g. Google Maps Api Key etc.) as well as you can change different **configuration settings** as follows:

Go to the `Api & Config` section.

* Provide `Google Maps Api Key` in the respective field.  
  > **Google Maps Api Key** is prerequisite. If you do not have *Google Maps Api Key*, you can aquire key by following these steps:   
    1. [Setup Google Cloud Project Console](../tools/setup_google_cloud.md)
    2. Once you have setup the project on [Google Cloud](https://developers.google.com/maps/documentation/android-sdk/start#get-key), you need to acquire the [Key](https://developers.google.com/maps/documentation/android-sdk/get-api-key).
 * Provide `Android/IOS Native Ad Id` in the respective fields.  
   > **AdMob App ID** is prerequisite. If you do not have *AdMob App ID*, you can aquire *AdMob App ID* by registering your app as an AdMob app. Simply follow these steps:   
    1. [Sign in](https://admob.google.com/home/) to or [Sign up](https://support.google.com/admob/answer/7356219) for an AdMob account.
    2. Register your app with AdMob. This step creates an AdMob app with a unique AdMob App ID for each platform.  
* If your website use `wp/v2/property` or `wp/v2/translated_property_name` instead of `wp/v2/properties`, then define *property* or *translated_property_name* as **Rest Api Properties Route**.
* If your website use `wp/v2/houzez_agent` or `wp/v2/translated_agent_name` instead of `wp/v2/agents`, then define *houzez_agent* or *translated_agent_name* as **Rest Api Agent Route**.
* If your website use `wp/v2/houzez_agency` or `wp/v2/translated_agency_name` instead of `wp/v2/agencies`, then define *houzez_agency* or *translated_agency_name* as **Rest Api Agency Route**.
* If you want to **limit** the `Places Api` to specific *country* or *countries*, follow these steps:  
  1. **Check mark** the *lock Places Api to specific country or countries* checkbox.
  2. Specify **Country/Countries Tags** (e.g. US, UK etc.) in required field.
* You can *enable* or *disable* `Social Sign-On` (i.e. Sign-in with *Facebook*, *Google* and *Apple*.)
    > *Sign-in with Apple* is only available in **IOS**.  
    > Prerequisite: [Social Sign-on Configuration](../tools/social_signon.md).
