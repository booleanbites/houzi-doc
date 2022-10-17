---
title: Language name in URL as Parameter/Directory for localized data from server
category: Tools Setup
order: 22
---

If you want to get localized data from server you can add language name as Parameter or Directory. There is a third option if you do not add language name. 

Open the `Project_HOME > assests > configuration > configuration.json` file, and look for the `locale_in_url` key. 
If you want to add language name as parameter set the value `Language name as parameter`, like following:

```
    ...
    "locale_in_url": "Language name as parameter",
    ...
```

If you want to add language name as directory set the value `Language name as directory`, like following:

```
    ...
    "locale_in_url": "Language name as directory",
    ...
```

If you want to do not want both of them set the value `Do not change url`, like following:

```
    ...
    "locale_in_url": "Do not change url",
    ...
```