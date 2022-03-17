---
title: Setup signing key for iOS Project
category: Tools
order: 10
---

For uploading apps to AppStore, you need to sign your builds with provisioning profile.
A provisioning profile is coupled with a SigningCertificate.  Follow instructions here:

https://help.apple.com/xcode/mac/current/#/dev60b6fbbc7

Once you have acquired a provisioning profile. Open Xcode and on the left file explorer menu, Find Runner (project name, mostly on top left). Click on that, you should see some configurations on the center pane. Goto Signing and Capabilities tab and select your team, profile, certificates

> **Note**: Apple Developer account is required for this step. 
