---
title: Text Form Field Configuration
category: Hooks & Widgets
permalink: hooks-widgets/text_form_field_configuration
order: 335
---

Houzi proivdes you with the **getTextFormFieldWidgetHook()**  to configure the **Text Form Field** throughout the app.  Simply open the file from the following path:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getTextFormFieldWidgetHook()` method.

```dart
@override
  TextFormFieldWidgetHook getTextFormFieldWidgetHook() {
    TextFormFieldWidgetHook textFormFieldWidgetHook = (
        context,
        labelText,
        hintText,
        additionalHintText,
        suffixIcon,
        initialValue,
        maxLines,
        readOnly,
        obscureText,
        controller,
        keyboardType,
        inputFormatters,
        validator,
        onSaved,
        onChanged,
        onFieldSubmitted,
        onTap,
    ) {

      Widget? textFormFieldWidget;
      return textFormFieldWidget;
    };

    return textFormFieldWidgetHook;
  }
```

Simply define your custom Text Form Field widget against the **textFormFieldWidget** as follows:


```dart
...
      Widget? textFormFieldWidget = YOUR_CUSTOM_WIDGET_HERE();
      return textFormFieldWidget;
    };

    return textFormFieldWidgetHook;
  }
```

> After modifications, restart the app and the changes will reflect in your app.