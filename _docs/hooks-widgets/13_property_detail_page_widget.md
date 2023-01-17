---
title: Change design of any section in Property Detail Page
category: Hooks & Widgets
permalink: property_details_customization
order: 13
---

If you want to change the design of any section in Property detail page, you need to open following file:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getWidgetHook()` method. The sections are provided to you, look for your desired section and pass it the widget that you want to replace. eg: 
```
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
        article.content,
        maxLines: 5,
        overflow: TextOverflow.ellipsis,
        textAlign: TextAlign.justify,
      );
```

