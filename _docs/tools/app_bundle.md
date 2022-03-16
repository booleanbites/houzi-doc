---
title: App bundle identifier & version
category: Tools
order: 4
---


> **Mandatory** App bundle identifiers are unique identifiers for your apps, they’re globally unique. Most of the time, you can reverse your website domain to create an identifier for your app. For example: `com.domain.app_name`

Once you’ve decided the unique identifiers, you need to replace existing with your own:

## Android:

you’ve to change package info in two places. Build.gradle and AndroidManifest.xml

### Change applicationId in build.gradle:

Open following file:

`Project_HOME > android > app > build.gradle`

Look for `applicationId` and replace the value with your own.

Look for `versionCode` and replace the value with your own. `versionCode` is for developers to keep track of builds.

Look for `versionName` and replace the value with your own. `versionName` is for the public.


### Change package in AndroidManifest.xml:


go to `houzi > android > app > src > main >  AndroidManifest.xml`

And replace the second attribute in the very first tage `package="com.houzi.app"` with your own package name.

if you change this package, change the folder structure of the kotlin classes as well, like below

`android > app > src > main > kotlin > your > package > name > all_kotlin_files`

We suggest renaming the folders manually using Finder or Windows Explorer. Then change the package declaration in kotlin files as well, for example in kotlin files change this line :
```
package com.houzi.app
```


To your own package like this:


```
package your.package.name
```

## iOS:
For iOS, open Xcode, and click on the project name (Runner) on the top left side and click on General tab, you should see the Bundle Identifier option, change its value with your own.

```
open: Project_HOME > ios > Runner > General > Bundle Identifier
```

**Bundle Identifier** - app’s unique identifier.

**Version** - app’s public version.

**Build** - app’s build code for developers to keep track.