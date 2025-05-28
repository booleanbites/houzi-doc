---
title: Hide Fields in Edit Profile
category: Hooks & Widgets
permalink: hooks-widgets/edit_profile_show_field
order: 341
---

# EditProfileShowFieldHook

Houzi provides you with the **`EditProfileShowFieldHook()`** which allows you to dynamically **show or hide specific profile fields** in the Edit Profile screen—such as Facebook, Instagram, WhatsApp, etc.

This can be useful for customizing which fields are visible based on your app’s requirements.

## File Location

`Project_HOME  > lib > hooks_v2.dart`
To edit this hook, open the following file in your project:

## How It Works

The `EditProfileShowFieldHook()` is a hook function that returns a function (`EditProfileShowFieldHook`) which takes a `fieldName` as a `String` and returns a `bool` (or `null`) based on whether you want the field to be shown or hidden.

- `true` → **Show** the field  
- `false` → **Hide** the field  
- `null` → **Default behavior (no override)**  

## Code Example

```dart
EditProfileShowFieldHook getEditProfileShowFieldHook() {
  EditProfileShowFieldHook editProfileShowFieldHook = (String fieldName) {
    
    if (fieldName == "facebook") {
      return true; // Show Facebook field
    } else if (fieldName == "phone") {
      return true; // Show Phone field
    } else if (fieldName == "instagram") {
      return false; // Hide Instagram field
    } else if (fieldName == "whatsApp") {
      return true; // Show WhatsApp field
    } else if (fieldName == "youtube") {
      return true; // Show YouTube field
    } else if (fieldName == "pinterest") {
      return true; // Show Pinterest field
    } else if (fieldName == "title_position") {
      return true; // Show Title Position field
    } else if (fieldName == "tax_number") {
      return false; // Hide Tax Number field
    } else if (fieldName == "website") {
      return true; // Show Website field
    }

    return null; // Return null if no condition matched (default behavior)
  };

  return editProfileShowFieldHook;
}
```

>  After modifications, restart the app and the changes will reflect in your app.

*Added in version 1.4.4*