---
title: Changing Theme Colors
category: App Setup
permalink: app-setup/change_app_theme
order: 205
---

## Change Theme Colors by Houzi Config
 You can use Houzi Config Builder to change [Theme Colors](/houzi-config-builder/change-theme) and many other options. 


## Change Theme Colors by config.json
 You can change colors from config by replacing ******* with your own color code. Open the `Project_HOME > assests > configuration > configuration.json` file, and look for the following keys:

**Note**: The `FF`, `4D`, `99` are used for opacity, if you want to change the opacity then modify them otherwise leave it as it is: 

 ```json
 "primary_color": "#FF******",
  "secondary_color": "#FF******",
  "icon_tint_color": "#FF******",
  "bottom_tab_bar_tint_color": "#FF******",
  "slider_tint_color": "#FF******",
  "selected_item_background_color": "#4D******",
  "un_selected_item_background_color": "#1A808080",
  "selected_item_text_color": "#FF******",
  "un_selected_item_text_color": "#8A000000",
  "action_button_background_color": "#FF******",
  "featured_label_background_color": "#99******",
 ```

> **Note**: If you didn't update the version number of config, then you will need to remove the existing app and re-install on device.

