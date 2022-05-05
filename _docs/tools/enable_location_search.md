---
title: Setup Places Api & Location Search
category: Tools Setup
order: 8.1
---

Enabling location autocomplete is done in two steps as follow:

#### Enable Place API on Google Cloud
Once you have setup the project on Google Cloud, you need to enable the places api in your project on your Google Project console, in order to get the location search in filter page working. You can enable Places API here: [Enable Places API](https://console.cloud.google.com/apis/library/places-backend.googleapis.com)

[Billing setup](https://console.cloud.google.com/projectselector/billing) is required for each project, but you will only be charged if a project exceeds its free quota. [Here you can read about billing and free quota](https://developers.google.com/maps/billing-and-pricing/billing#monthly-credit)

#### Enable Location option in Houzi

Once you've enabled Places API and billing on your project, you need to enable location search in Flutter source code, here's how you can do that:

Go to the `houzi > packages > houzi_package > lib > common > constants.dart` file, and look for `SHOW_LOCATION_ON_FILTER_PAGE = 1;` and set its value to `1`.

Relaunch the app, and you should see the location selection on the filter search page.