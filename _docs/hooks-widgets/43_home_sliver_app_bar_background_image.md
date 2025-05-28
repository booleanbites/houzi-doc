---
title: Home Background Hook
category: Hooks & Widgets
permalink: hooks-widgets/home_sliver_app_bar_background_image
order: 343
---

# HomeSliverAppBarBGImageHook

Houzi provides the **`HomeSliverAppBarBGImageHook()`** to **customize the background image** displayed in the Sliver AppBar on the home screen. This hook allows you to either:

- Set a **custom background image** from your assets, or  
- Return **null** to use no background image (default behavior).

## How It Works

The `HomeSliverAppBarBGImageHook()` returns a function that provides a `String?` path to your background image asset. This path defines which image should be displayed as the background in the home screen's Sliver AppBar.

- Return a valid asset path → to **display a custom background image**
- Return `null` → to **use no background image**

```dart
HomeSliverAppBarBGImageHook getHomeSliverAppBarBGImageHook() {
  return (BuildContext context) {
    String? _backgroundImage;
    
    // Example asset paths:
    // _backgroundImage = "assets/image/any_image.png";
    // _backgroundImage = "assets/settings/dummy_property_image_01.jpg"; // For Test
    
    // Return the background image path
    // return _backgroundImage;
    
    // If you don't want to use background image, return null
    return null;
  };
}
```

## Asset Configuration

Make sure your  `pubspec.yaml` is properly configured to load your background image:

```yaml
flutter:
  assets:
    - assets/image/
    - assets/settings/
```

## Usage Examples

### Example 1: Using a Custom Background Image

```dart
HomeSliverAppBarBGImageHook getHomeSliverAppBarBGImageHook() {
  return (BuildContext context) {
    String? _backgroundImage = "assets/image/home_background.png";
    return _backgroundImage;
  };
}
```

### Example 2: Conditional Background Based on Context

```dart
HomeSliverAppBarBGImageHook getHomeSliverAppBarBGImageHook() {
  return (BuildContext context) {
    // You can use context to determine which image to show
    bool isDarkMode = Theme.of(context).brightness == Brightness.dark;
    
    String? _backgroundImage = isDarkMode 
        ? "assets/image/dark_home_bg.png"
        : "assets/image/light_home_bg.png";
        
    return _backgroundImage;
  };
}
```

### Example 3: No Background Image

```dart
HomeSliverAppBarBGImageHook getHomeSliverAppBarBGImageHook() {
  return (BuildContext context) {
    // Return null for no background image
    return null;
  };
}
```

## Best Practices

- **Image Size**: Use appropriately sized images to avoid memory issues
- **Aspect Ratio**: Consider different screen sizes and orientations
- **File Size**: Optimize images to reduce app bundle size
- **Performance**: Large images may impact scrolling performance

> ⚠️ **Important**  
> Ensure your image assets are properly added to your `pubspec.yaml` file and exist in the specified directories. Missing assets will cause runtime errors.

> After modifications, restart the app and the changes will reflect in your app.

*Added in version 1.4.4*