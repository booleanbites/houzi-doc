---
title: Text Form Field Customization
category: Hooks & Widgets
permalink: hooks-widgets/text_form_field_customization
order: 334
---

Houzi proivdes you with the **getTextFormFieldCustomizationHook()**  to customize the **Text Form Field** throughout the app.  Simply open the file from the following path:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getTextFormFieldCustomizationHook()` method:

```dart
@override
  TextFormFieldCustomizationHook getTextFormFieldCustomizationHook() {
    TextFormFieldCustomizationHook textFormFieldCustomizationHook = () {
      Map<String, dynamic> textFormFieldCustomizationMap = {
        'labelTextStyle' : null,
        'hintTextStyle' : null,
        'additionalHintTextStyle' : null,
        'backgroundColor' : null,
        'focusedBorderColor' : null,
        'hideBorder' : null,
        'borderRadius' : null,
      };

      return textFormFieldCustomizationMap;
    };

    return textFormFieldCustomizationHook;
  }
```

You can customize following attributes of *Text Form Field*:

- Label TextStyle.
- Hint TextStyle.
- Additional Hint TextStyle.
- Background Color.
- Focused Border Color.
- Hide Border.
- Border Radius.

Let's dive into the details of each attribute customization.


### Label TextStyle

**Label** is the title of the text form field. If you do not want to use the default Houzi Label TextStyle, you can define your custom label textstyle and instead of returning **null** against the **'labelTextStyle'** key in the **textFormFieldCustomizationMap**, return your custom textstyle for label.

### Hint TextStyle

**Hint** is the helping text provided as the placeholder text inside the empty text form field. If you do not want to use the default Houzi Hint TextStyle, you can define your custom hint textstyle and instead of returning **null** against the **'hintTextStyle'** key in the **textFormFieldCustomizationMap**, return your custom textstyle for hint.

### Additional Hint TextStyle

**Additional Hint** is the helping text provided below the text form field for some additional guidance. If you do not want to use the default Houzi Additional Hint TextStyle, you can define your custom additional hint textstyle and instead of returning **null** against the **'additionalHintTextStyle'** key in the **textFormFieldCustomizationMap**, return your custom textstyle for additional hint.

### Background Color

**Background Color** is the background color of the text form field. If you do not want to use the default Houzi Background Color for the text form field, you can define your custom background color and instead of returning **null** against the **'backgroundColor'** key in the **textFormFieldCustomizationMap**, return your custom background color.

### Focused Border Color

**Focused Border Color** is the border color of the text form field when the user interacts with it. If you do not want to use the default Houzi Focused Border Color for the text form field, you can define your custom focused Border color and instead of returning **null** against the **'focusedBorderColor'** key in the **textFormFieldCustomizationMap**, return your custom focused Border color.

### Hide Border

If you do not want to show border around the text form field, instead of returning **null** against the **'hideBorder'** key in the **textFormFieldCustomizationMap**, return **true**.

### Border Radius

**Border Radius** is the radius of borders of the text form field. If you do not want to use the default Houzi Border Radius, you can define your custom border radius and instead of returning **null** against the **'borderRadius'** key in the **textFormFieldCustomizationMap**, return your custom border radius.


> After modifications, restart the app and the changes will reflect in your app.