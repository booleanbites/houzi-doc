---
title: Localized URL for WPML
category: App Setup
permalink: app-setup/app_url_localization
order: 208
---

When you're using WPML, you provide localization of your data on langugage specific URL of your website. It can either be a parameter `(domain.com/?lang=en, domain.com/?lang=fr)` or it can be a subdirectory `(domain.com/en, domain.com/fr)`. The REST API provide localized data on localized URL. So if you want to get localized data from server you can add language name as Parameter or Directory. There is a third option if you do not want to add language name to the URL.

Open the `Project_HOME > assests > configuration > configuration.json` file, and look for the `locale_in_url` key. 
If you want to add language name as parameter set the value `Language name as parameter`, like following:

```json
    ...
    "locale_in_url": "Language name as parameter",
    ...
```

If you want to add language name as directory set the value `Language name as directory`, like following:

```json
    ...
    "locale_in_url": "Language name as directory",
    ...
```

If you want to do not want both of them set the value `Do not change url`, like following:

```json
    ...
    "locale_in_url": "Do not change url",
    ...
```

You can also change these option from Houzi Builder Api & Config section.