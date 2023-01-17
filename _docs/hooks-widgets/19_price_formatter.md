---
title: Set Price Format
category: Hooks & Widgets
permalink: price_formatter_customization
order: 19
---

You can set your own price format method in app. There are two price formatter using in Houzi. 

1. If you want to format price in Property detail page or any other place, use this method. If you want to use Houzi pre define formatter than return null. Go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getPriceFormatterHook()` method. For e.g:

```
static getPriceFormatterHook() {
    PriceFormatterHook priceFormatterHook = (String propertyPrice, String firstPrice) {
      // Define your own method here and return the formatted string
      return null; 
    };

    return priceFormatterHook;
  }
```

2. If you want to format price on Property Card use this method. If you want to use Houzi pre define formatter than return null. Go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getCompactPriceFormatterHook()` method. For e.g:

```
static getCompactPriceFormatterHook() {
    CompactPriceFormatterHook compactPriceFormatterHook = (String inputPrice) {
      // Define your own method here and return the formatted string
      return null;
    };

    return compactPriceFormatterHook;
    
  }
```

