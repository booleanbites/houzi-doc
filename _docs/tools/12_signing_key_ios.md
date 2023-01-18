---
title: Setup signing for iOS Project
category: Tools Setup
permalink: tools/setup_ios_signing
order: 12
---

For uploading apps to AppStore, you need to sign your builds with provisioning profile.
A provisioning profile is coupled with a SigningCertificate.

> **Note**: Apple Developer account is required for this step. Make sure to buy one before continuing.

There're two ways to setup signing for your iOS app, one is doing everything manual, and second is doing automatic signing.

### Automatic Signing
In modern Xcode, when you use automatic signing to let Xcode do everything required to sign the app. Here're the steps:

1. Make sure you have setup your [app identifier](app-setup/change_app_identifier) and [app name](app-setup/change_app_display_name) before setting up signing.
2. Login your apple id in Xcode by going to top left Xcode > preferences menu (CMD + ,) and switch to Accounts tab.
3. Now tick the automatic signing checkbox and select your team in project signing tab of project info `Xcode Project > Runner > Signing & Capabilities > Team`
4. Connect a physical device (iPhone) and press Repair.
5. It should create your app id, signing certificate, provisioning profile, add your device id to your Apple Developer Portal.

For full instructions, read through here:
https://help.apple.com/xcode/mac/current/#/dev60b6fbbc7

### Manual Signing

The manual signing requires some steps that need to be performed and the process to do so may vary on different MacOS, Xcodes and environment. The essential steps required are listed below:

- Open your Apple Developer Portal.
- Create your app identifier.
- Create a signing key and CSR (certificate signing request) in your keychain, and get a development/release certificate from Apple Developer.
- Download the certificate and add to your keychain.
- Register a device by entering its UDID.
- Create a development/release signing profile.
- Download the signing profile and open in Xcode.
- Select the certificate and signing profile and team in Build Setting of the project.
- You should be ready to compile.

The manual process is sometimes necessary to enable certain features, so its better to follow online latest guideline to do do this process manually.

Full instructions to manually sign the app can found here: [Manually sign an app](https://help.apple.com/xcode/mac/current/#/dev1bf96f17e)



