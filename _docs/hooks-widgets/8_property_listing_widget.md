---
title: Change design of Property listing
category: Hooks & Widgets
permalink: hooks-widgets/property_item_design_custom
order: 308
---

If you want to change property listing, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

# Set the Height of Design

Look for the `getPropertyItemHeightHook()` method. Return the height (in double, e.g. return 200;) instead of returning null.

### Example Code:

```dart
  …
   @override
  PropertyItemHeightHook getPropertyItemHeightHook() {
    PropertyItemHeightHook propertyItemHeightHook = (String designName) {

        return null;
    };
    return propertyItemHeightHook;
  }
  …
```

# Set the Widget of Design

Look for the `getPropertyItemHookV2()` method. You are provided with the following parameters:  
- aritcle.
- designName.
- heroId.
- onTap.

### article: 

aritcle is the instance of property/listing item. You can get the listing related information (e.g. Listing's title, price etc.) from it. 

### designName:

designName is a String parameter. If you want to use specific design for specific type of listing item/items, you can use the designName to achieve this purpose.

> Whe you select the "item_design_form_hook" option form the dropdown menu of layout designs, the Title of that widget will be provided to you as the designName so if you want, you can provide seperate listing design for that paritcular listing section.

### heroId:

By default, the listings provided by the Houzi app uses the Hero widget for smooth transititon between listing item and listitng item profile. If you want to take advantange of this Hero widget, you can use the *heroId* in the **tag** of your Hero widget.

### onTap:

onTap is the default call back provided by the Houzi app. If you want to use the default call back on the listing item, then use the **onTap**.


## Example Code:

```dart
  …
    @override
  PropertyItemHookV2 getPropertyItemHookV2() {
    PropertyItemHookV2 propertyItemHookV2 =
        ({required article, required designName, required heroId, required onTap}) {

      // Return your designName specific listing design widget here
     if (designName == 'Featured Properties') {
        return YOUR_SPECIFIC_DESIGN_WIDGET_HERE or null;
      }

      // Return your global listing design widget here
      return YOUR_GLOBAL_DESIGN_WIDGET_HERE or null;
    };

    return propertyItemHookV2;
  }
  …
```


# Deprecated Hook

> Following is the description of depricated hook. We recommend you to use the **PropertyItemHookV2**.

Look for the `getPropertyItemHook()` method. The Property/Article instance is provided to you, return the widget that you want to show. eg: 
```dart
  …
    PropertyItemHook propertyItemHook = (BuildContext context, Article article) {

      return YOUR_GLOBAL_DESIGN_WIDGET_HERE or null;

    };
  …
```

