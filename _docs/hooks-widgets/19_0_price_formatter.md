---
title: Set Price Format
category: Hooks & Widgets
permalink: hooks-widgets/price_formatter_customization
order: 319
---

In the Houzi app, you have the flexibility to set your own price format methods. There are two price formatters used in different parts of the app.

### 1. Formatting Price in Property Detail Page or Other Places

If you want to format the price in the Property Detail page or any other place, follow these steps:

1. Locate the file `hooks_v2.dart` in your project. The path is `Project_HOME > lib > hooks_v2.dart`.

2. Look for the method `getPriceFormatterHook()` in the `hooks_v2.dart` file.

3. Inside the `getPriceFormatterHook()` method, define your own method to format the price and return the formatted string. If you prefer to use the default Houzi formatter, you can simply return `null`. Here's an example:

   ```dart
   @override
   PriceFormatterHook getPriceFormatterHook() {
     PriceFormatterHook priceFormatterHook = (String propertyPrice, String firstPrice) {
       // Define your own method here and return the formatted string
       return null;
     };

     return priceFormatterHook;
   }
   ```

### 2. Formatting Price on Property Card

If you want to format the price on the Property Card, follow these steps:

1. Open the file `hooks_v2.dart` in your project. The path is `Project_HOME > lib > hooks_v2.dart`.

2. Locate the method `getCompactPriceFormatterHook()` in the `hooks_v2.dart` file.

3. Inside the `getCompactPriceFormatterHook()` method, define your own method to format the price and return the formatted string. If you prefer to use the default Houzi formatter, you can return `null`. Here's an example:

   ```dart
   @override
   CompactPriceFormatterHook getCompactPriceFormatterHook() {
     CompactPriceFormatterHook compactPriceFormatterHook = (String inputPrice) {
       // Define your own method here and return the formatted string
       return null;
     };

     return compactPriceFormatterHook;
   }
   ```

### 3. Displaying Full Price on Property Card

If you want to show the full price on the Property Card, you can use the following code in the `getCompactPriceFormatterHook()` method:

```dart
@override
CompactPriceFormatterHook getCompactPriceFormatterHook() {
  CompactPriceFormatterHook compactPriceFormatterHook = (String inputPrice) {
    // Use the utility method priceFormatter to format the price
    return UtilityMethods.priceFormatter(inputPrice, "");
  };

  return compactPriceFormatterHook;
}
```

By following these instructions, you can customize the price formatting in the Houzi app according to your requirements.