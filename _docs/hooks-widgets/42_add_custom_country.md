---
title: Direct Messages Hooks
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_country
order: 342
---

# CustomCountryHook

Houzi provides the **`CustomCountryHook()`** to **customize the country calling codes** available in the phone field. This hook allows you to either:

- Show **all countries** (default), or  
- Limit the list to **specific countries** based on your app’s requirements.

## Required Package

Make sure to include the following dependency in your project pubspec.yaml:
Add the above dependency in:

`[houzi-directory]/pubspec.yaml`

```yaml
intl_phone_field: 3.2.0
```

## Import Statement

To Modify the hook and to use the Country model, add the following import in your hooks_v2.dart file at `Project_HOME > lib > hooks_v2.dart`:

`import 'package:intl_phone_field/countries.dart';`


## How It Works

The `CustomCountryHook()` returns a function that provides a list of `Country` objects. This list defines which countries (and their respective phone codes) should be shown in the phone number field.

- Return a list of specific countries → to **limit options**
- Return `null` → to **show all countries by default**

```dart
CustomCountryHook getCustomCountryHook() {
  CustomCountryHook customCountryHook = () {
    List<Country> countryList = [
      Country(
        code: "PK",
        dialCode: "92",
        name: "Pakistan",
        flag: '🇵🇰',
        nameTranslations: {},
        minLength: 10,
        maxLength: 10,
      ),
      Country(
        code: "RU",
        dialCode: "7",
        name: "Russia",
        flag: '🇷🇺',
        nameTranslations: {},
        minLength: 10,
        maxLength: 10,
      ),
    ];

    // Return this list to show only selected countries
    // return countryList;

    // Return null to show all countries by default
    return null;
  };

  return customCountryHook;
}
```

## Country Field Reference Table

| Property           | Description                              | Example             |
| ------------------ | ---------------------------------------- | ------------------- |
| `code`             | 2-letter ISO country code                | `"PK"` for Pakistan |
| `dialCode`         | Country calling code                     | `"92"`              |
| `name`             | Country name                             | `"Pakistan"`        |
| `flag`             | Country flag emoji                       | `'🇵🇰'`               |
| `nameTranslations` | Country name translations (can be empty) | `{}`                |
| `minLength`        | Minimum phone number length              | `10`                |
| `maxLength`        | Maximum phone number length              | `10`                |


## Emoji Tips for Flags

To correctly display country flags using emoji, follow the platform-specific instructions below:

### On macOS:
- Press `Control` + `Command` + `Space` to open the emoji picker.
- Search for the country (e.g., `Pakistan`).
- Click on the 🇵🇰 flag emoji to insert it.

### On Windows:
- Press `Windows` + `.` (period) to open the emoji panel.
- Search for the country (e.g., `United Kingdom`).
- Select the 🇮🇳 flag emoji from the list.

> ⚠️ **Important**  
> Ensure you're using **valid Regional Indicator Symbols**.  
> Using incorrect or unsupported emoji may result in display/rendering issues or show as blank squares or placeholders.




>  After modifications, restart the app and the changes will reflect in your app.

*Added in version 1.4.4*