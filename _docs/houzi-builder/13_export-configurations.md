---
title: Export Configuration
category: Houzi Builder
permalink: houzi-builder/export_configuration
order: 413
---

> **Important**: You are required to install the Houzi Rest Api Plugin on your Houzez wordpress. To install the Plug-in, click on [Houzi Rest Api Plugin Link](https://github.com/booleanbites/houzi-rest-api).

Once you have filled all the **required** fields, follow these steps: 

1. Press the **Export** button, at the top-right side of screen. A dialogbox will open with preview of the configurations of your app.

    <img src="../../images/export-config-01.png" alt="export-config-01" title="export-config-01" border= "1px solid"/>

    <img src="../../images/export-config-02.png" alt="export-config-02" title="export-config-02" border= "1px solid"/>
     

2. At the bottom of dialogbox, there is **Copy** button. Press the *Copy* button and the configurations of your app will be copied to clipboard.

3. Open the **configurations.json** from the project and paste the *copied configurations* in it replacing the old configurations.  
 
    > *configurations.json* file path:  `Project_HOME > assets > configurations > configurations.json`

4. **[Optional Task]** At the bottom of dialogbox, you will see a checkbox named as **Increase configurations version number**. If you are [**Editing/Updating**](/houzi-builder/edit_configuration) the configurations of your app, then *checkmark* it, else leave it unchecked.  

> **Important**: If app receives the same version number in configurations, then it'll not honor the new configurations having the same config version. So if you don't increase the version number while exporting, then delete the existing app from device and reluanch to view the changes.