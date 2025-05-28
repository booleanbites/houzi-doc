---
title: Phone Signup Countries
category: Hooks & Widgets
permalink: hooks-widgets/add_custom_country
order: 342
---



Houzi provides the **`CustomCountryHook()`** to **customize the country list** available in the phone signup page. This hook allows you to either:

- Show **all countries** (default), or  
- Show specific **countries**.


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
- Select the 🇬🇧 flag emoji from the list.

> ⚠️ **Important**  
> Ensure you're using **valid Regional Indicator Symbols**.  
> Using incorrect or unsupported emoji may result in display/rendering issues or show as blank squares or placeholders.


>  After modifications, restart the app and the changes will reflect in your app.

*Added in version 1.4.4*