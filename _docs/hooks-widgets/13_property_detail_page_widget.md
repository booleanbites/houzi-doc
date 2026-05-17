---
title: Design sections in Property Details
category: Hooks & Widgets
permalink: hooks-widgets/property_details_customization
order: 313
---

Houzi provides you with the option to completely customize your Property Details Screen. You can provide your own custom widgets if you do not want to utilize the default Houzi widgets for the Property details screen. 
 
 Simply open the file from the following path:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getWidgetHook()` method. You are provided wtih the following parameters: 

- context.
- article.
- hook.

#### context 

The parameter *context* is of the type of *Build Context*. If you wnat to provide a inline widget you can use this context widget.

> It is recommended that you use proper widget (stateless or stateful) instead of using inline or function widgets.

#### article

The parameter *article* is property object whose details are being displayed. If you are providing your custom widget then you will need the property object data to display in your widget e.g. Tiltle or Address of property etc. 

You can visit the following file to learn more about *article*.

`Project_HOME > packages > houzi_package > lib > models > article.dart`

#### hook

The parameter *hook* represents the identifier for the widget being built. 

- **For Built-in Widgets**: The *hook* represents the name of the Houzi default Section/Widget (e.g., `'article_title'`, `'article_description'`).
- **For Custom Widgets**: If you add a custom section with `widget_type: "place_holder"`, the *hook* parameter will match the `widget_title` you defined in the configuration.

If you provide your custom widget against the desired hook, the default Houzi widget (or an empty space) will be replaced with your custom widget.

### Hook

Following is the glimpse of the **getWidgetHook()**. You can provide your custom widget against any desired section/widget just by simply returning your custom widget instead of returing **null**.

```dart
  …
   @override
  PropertyPageWidgetsHook getWidgetHook() {
    PropertyPageWidgetsHook detailsHook = (
      BuildContext context,
      Article article,
      String hook,
    ) {
      if (hook == 'article_images') {
        return null;
      } else if (hook == 'article_title') {
        return null;
      } else if (hook == 'article_address') {
        return null;
      } 
  …
```

### Example

You have a custom widget named as **customDescriptionWidget()** and you want to use this widget instead of default Houzi **Description** widget on the Property Details Screen. You can simply replace the null with your custom widget against the "article_description" hook as follows:

```dart
  …
    else if (hook == 'article_features') {

        return null;
    } else if (hook == 'article_description') {
      
        return customDescriptionWidget(context, article);
    } else if (hook == 'article_address_info') {

        return null;
    }
  …

// your customDescriptionWidget 
static Widget customDescriptionWidget(BuildContext context, Article article) {
    return Text(
        article.content ?? "",
        maxLines: 5,
        overflow: TextOverflow.ellipsis,
        textAlign: TextAlign.justify,
      );
```

> After modifications, restart the app and the changes will reflect in your app.