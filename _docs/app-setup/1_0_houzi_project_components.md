---
title: Houzi Project Components
category: App Setup
permalink: app-setup/houzi_project_components
order: 201
---

<br/>
<iframe width="560" height="315" src="https://www.youtube.com/embed/0-5-glZjV5A" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br/>
<br/>

The **Houzi** project is a real estate app designed using Flutter and includes several essential components. This document outlines the major parts of the project and their purpose, providing developers with a comprehensive understanding of how each piece works.

## 1. Flutter Project

This is the main part of the Houzi project and follows a standard Flutter project structure. The Flutter project contains two critical files:
- **main.dart**: The entry point of the app, handling initialization and app flow. Developers can modify this file to add features like onboarding screens or other introductory content before the app's main processes start.
- **hooks_v2.dart**: This file contains hooks that allow customization of various options in the app, such as changing layouts or adding custom designs for multiple components. A complete list of customizable options is available in this documentation.

## 2. Houzi Package Dependency

The **houzi_package** is the core of the app, containing all of the code that powers Houzi's features and functionality. While the Flutter project depends on this package, it exists as a separate component. This separation allows for easier upgrades when a new version of Houzi is released.

#### Key Points:
- Houses the primary functionality of the Houzi app.
- Easy to replace during version upgrades without modifying the main project.

## 3. Android Native Project

The **Android native project** is the part that interacts with Android-specific functionalities like Firebase, push notifications, and Android-specific permissions.
You will need to edit following things when configuring the project for the first time.

- App icon
- App name and package identifier
- Firebase and GoogleCloud setup
- OneSignal Push setup 
- Keystore setup (important for signing the app)

Once set up initially, updates to the houzi_package usually do not require editing the Android project files.

## 4. iOS Native Project

Similar to the Android native project, the **iOS native project** is responsible for iOS-specific features like push notifications and deep linking.
You will need to edit following things when configuring the project for the first time.
- App icon
- App name and package identifier
- Firebase and GoogleCloud setup
- OneSignal Push setup
- Signing profiles (for App Store distribution)

This part generally doesn't need editing when updating the houzi_package unless you need to change core settings or app branding.

## 5. Assets Directory

The **assets** directory contains all the static files used by the app, including:
- **Configurations**: Important settings like business branding, layout options, and website URLs are stored here.
- **Localization**: Language and region-specific resources for supporting multiple languages.
- **Icons and Fonts**: Custom icons and fonts used in the app’s design.

Typically, this directory remains unchanged when upgrading the houzi_package unless you need to update your custom branding or design elements.

## 6. Configurations JSON File

The **configurations.json** file is a vital part of the app’s customization. It includes:
- **Business branding**: Colors, logos, and other branding information.
- **Layout options**: Customizations for home screens, listing details, and menus.
- **Search filters**: Configurations for how property search works in the app.
- **Website address**: URL of the connected WordPress site.
- **Menu structure**: How the app’s navigation menu is set up.

#### Importance:
- **Business Customization**: Allows you to fully customize the app to match your business branding.
- **Layout Flexibility**: Enables the setup of different home layouts, listing structures, and navigation menus without touching the core app code.

--- 
### Important Notes:
- **Separation of Concerns**: The project is split into different components to make maintenance and updates easier. You often only need to replace the houzi_package when upgrading.
- **Branding and Customization**: The app is highly customizable through the `hooks_v2.dart` file and the configurations JSON file, allowing for deep personalization without modifying the core code.
- **Firebase and Push Notifications**: Ensure that your Firebase configurations are in place for analytics and push notifications.
  
--- 
