---
title: Property Valued Feature Design Hook
category: Hooks & Widgets
permalink: hooks-widgets/valued_feature_design_hook
order: 349
---

Houzi provides the **`getValuedFeatureDesignHook()`** to control the design/layout version of the property valued features section (bedrooms, bathrooms, garage, size, year built, etc.) displayed on the property details page.

## When to Use

Use this hook when you want to choose between the two supported valued feature layouts:
* **`v1`**: The original horizontal scrolling list design.
* **`v2`**: A new, modern rectangular 3-column grid design (default).

## How to Use

Open `hooks_v2.dart` and locate the **`getValuedFeatureDesignHook()`** method. If not available then copy and paste the code from here.

1. Set the design version string you want to return (`"v1"` or `"v2"`).
2. Return the design version from the function.
3. **Important**: Register this hook in your `lib/main.dart` inside the `hooksMap` by adding:
   ```dart
   hooksMap["valuedFeatureDesignHook"] = v2Hooks.getValuedFeatureDesignHook();
   ```

```dart
@override
ValuedFeatureDesignHook getValuedFeatureDesignHook() {
  ValuedFeatureDesignHook hook = () {
    /// Return "v1" for horizontal list design
    /// Return "v2" for 3-column grid design (default)
    return "v2";
  };
  return hook;
}
```

## Supported Layouts

### 1. Horizontal Scroll Layout (`v1`)
This is the original Houzi design. The features are displayed in a single-row horizontal scrolling card list.

### 2. 3-Column Grid Layout (`v2` - Default)
This is a modern grid layout where items are arranged in a 3-column structure. 
* Designed as compact rectangles (with a clean aspect ratio).
* Automatically aligns the icon, title (label), and value (e.g., "Bedroom", "2") to the left side of the rectangular card.
* Icons are colored neutrally (matching the text color instead of the primary theme color).

## Usage Example

```dart
@override
ValuedFeatureDesignHook getValuedFeatureDesignHook() {
  ValuedFeatureDesignHook hook = () {
    // Switch to the horizontal layout (v1)
    return "v1";
  };
  return hook;
}
```

> After modifications, restart the app and the changes will reflect in your app.
