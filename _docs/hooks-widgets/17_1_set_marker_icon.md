---
title: Set Custom Map Icon
category: Hooks & Widgets
permalink: hooks-widgets/custom_map_marker
order: 317
---

 Show custom marker in MapView instead of default Pin Point marker using this hook. First you have to go to `Project_HOME  > assets` folder and paste your image. Copy your image name and go to `PROJECT_HOME > pubspec.yaml` and specify image path in asset section e.g

```yaml
  ...
    assets:
      - assets/IMAGE-NAME.png
  ...
```

Then go to `Project_HOME  > lib > hooks_v2.dart`. Look for the `getMarkerIconHook()` method.

```dart
static getMarkerIconHook() {
    MarkerIconHook markerIconHook = () {
      // If you want to set the default Pin Point marker return null
      // else return the path of the image
      //
      //
      //return null;

      return "assets/IMAGE-NAME.png";
    };

    return markerIconHook;

  }
```

