---
title: Perform Action on Add Property
category: Hooks & Widgets
permalink: hooks-widgets/perform_action_on_add_property
order: 337
---

Houzi proivdes you with the **getAddPropertyActionHook()**  to perform some action on Add Property.  Simply open the file from the following path:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getAddPropertyActionHook()` method.

```dart
@override
  AddPropertyActionHook? getAddPropertyActionHook() {
    AddPropertyActionHook addPropertyActionHook = ({
      required context,
      required addPropertyNonce,
      required uploadImagesNonce,
      required addPropertyDataMap,
      required defaultAddPropertyFunc}) {
      // define your action here
    };

    // return addPropertyActionHook;
    return null;
  }
```

You are provided with the following parameter:

- [context](#context)  
- [addPropertyNonce](#addpropertynonce)  
- [uploadImagesNonce](#uploadimagesnonce)  
- [addPropertyDataMap](#addpropertydatamap)  
- [defaultAddPropertyFunc](#defaultaddpropertyfunc)  

Let's dive into the details of each parameter.

## context

context is the Build Context. You are provided with the context so you can perform build context related actions.

## addPropertyNonce

You are required to pass a Add Property Nonce aginst the **addPropertyNonce** key along the property data map for adding a property. You are provided with the addPropertyNonce for this purpose.

## uploadImagesNonce

You are required to pass a Upload Image Nonce aginst the **addPropertyImageNonce** key along the image data map for uploading an image. You are provided with the uploadImagesNonce for this purpose.

## addPropertyDataMap

You are provided with all the form fields related keys and values data e.g. Property Title and its user input etc. in the addPropertyDataMap. You can use this map for your custom actions.

## defaultAddPropertyFunc

If you want to perform some additional actions along the default Houzi Add Property Action, you can use the defaultAddPropertyFunc for this purpose.
Just define your additional actions and at the end use the defaultAddPropertyFunc.

For example:

```dart
@override
  AddPropertyActionHook? getAddPropertyActionHook() {
    AddPropertyActionHook addPropertyActionHook = ({
      required context,
      required addPropertyNonce,
      required uploadImagesNonce,
      required addPropertyDataMap,
      required defaultAddPropertyFunc}) {
      // define your action here
      actions();
     // use defaultAddPropertyFunc at the end
      defaultAddPropertyFunc();
    };

    // return addPropertyActionHook;
    return null;
  }
  ```

>  - Return `addPropertyActionHook` instead of null for the modifications to work. 

```dart
@override
  AddPropertyActionHook? getAddPropertyActionHook() {
    AddPropertyActionHook addPropertyActionHook = ({
      required context,
      required addPropertyNonce,
      required uploadImagesNonce,
      required addPropertyDataMap,
      required defaultAddPropertyFunc}) {
      // define your action here
    };

    return addPropertyActionHook;
  }
```

> - After modifications, restart the app and the changes will reflect in your app.