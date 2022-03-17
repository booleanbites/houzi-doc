---
title: Setup signing key for Android Project
category: Tools Setup
order: 9
---

For uploading apps to PlayStore, you need to sign your builds with uniquely generated keys and keystores. Follow instructions here:

https://developer.android.com/studio/publish/app-signing#generate-key

Once you have generated a keystore.jks, you need to replace the existing keystore here:

`Project_HOME > android > houzi_public_keystore.jks`

If you have different name, you need to update its reference in this file:

`Project_HOME > android > key.properties`

The `key.properties` file refers to path relevant to gradle location. So always consider adding a path with relation to the gradle file.