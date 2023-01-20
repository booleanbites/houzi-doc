---
title: Setup Places Api & Location Search
category: Tools Setup
permalink: tools/setup_places_api
order: 10
---

Enabling location autocomplete is done in three steps as follow:

## Enable Place API on Google Cloud
Once you have setup the project on Google Cloud, you need to enable the places api in your project on your Google Project console, in order to get the location search in filter page working. You can enable Places API here: [Enable Places API](https://console.cloud.google.com/apis/library/places-backend.googleapis.com)

[Billing setup](https://console.cloud.google.com/projectselector/billing) is required for each project, but you will only be charged if a project exceeds its free quota. [Here you can read about billing and free quota](https://developers.google.com/maps/billing-and-pricing/billing#monthly-credit)

## Setup maps api key
You need to set maps api key (also used for places api) in your application.
### Setup maps api key by Houzi Config
 You can use Houzi Config Builder to save the Maps api key: [Theme Api & Config](/houzi-builder/api_config_setup). 
### Or setup maps api key manually by editing config.json
 You can change colors from config by replacing ******* with your own color code. Open the `Project_HOME > assests > configuration > configuration.json` file, and look for the following keys:

 ```
  "google_map_api_key": "your_key_here",
  "lock_places_api": true,
  "lock_places_api_countries": "US,FR",
 ```

 > **Note**: The `lock_places_api`, `lock_places_api_countries` are used to lock places api suggestions to specific countries. You should definitely limit the countries to get the correct results.

### Enable Location option in Houzi Config Builder

Once you've enabled Places API and billing on your project, you need to enable location search via Houzi Config Builder. [Customize Search Screen](/houzi-builder/customize_search_filters)

Or you can manually look into  `Project_HOME > assests > configuration > configuration.json` and look for following keys:
```
{
    "section_type": "location_picker",
    "title": "City",
    ...
    "show_search_by_city": true,
    "show_search_by_location": false,
    ...
}
```
Set the `show_search_by_location` to `true` and you're done.
Relaunch the app, and you should see the location selection on the filter search page.