---
title: Export Configuration
category: Houzi Builder
permalink: houzi-builder/export_configuration
order: 410
---

> **Important**: You are required to install the Houzi Rest Api Plugin on your Houzez wordpress. To install the Plug-in, click on [Houzi Rest Api Plugin Link](https://github.com/booleanbites/houzi-rest-api).

Once you have filled all the required fields, follow these steps: 
1. Press the **Export** button. A dialogbox will open with preview of the configurations of your app.
    > `Export` button is on the right most side of top bar.  

    <img src="../../images/export-configurations-screenshot.png" alt="export-configurations-screenshot" title="export-configurations-screenshot" border= "1px solid"/>
2. At the bottom of dialogbox, there is **Copy** button. Press the `Copy` button and the configurations of your app will be copied to clipboard.
3. Open the `configurations.json` from the project and paste the *copied configurations* in it replacing the old configurations.  
 
    **configurations.json** file path:  
    `Project_HOME > assets > configurations > configurations.json`

1. **[Optional Task]** At the bottom of dialogbox, you will see a checkbox named as `Increase configurations version number`. If you are [**Editing/Updating**](/houzi-builder/edit_configuration) the configurations of your app, then *checkmark* it, else leave it unchecked.  
    
    <img src="../../images/export-configurations-increase-version-screenshot.png" alt="export-configurations-increase-version-screenshot" title="export-configurations-increase-version-screenshot" border= "1px solid"/>