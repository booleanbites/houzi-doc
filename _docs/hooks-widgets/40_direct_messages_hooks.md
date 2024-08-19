---
title: Direct Messages Hooks
category: Hooks & Widgets
permalink: hooks-widgets/direct_messages_hooks
order: 340
---

Direct Messages is one of the best way to contact the realtor. Houzi proivdes you with the **getThreadApiRefreshTimeHook()** and **getMessageApiRefreshTimeHook()**  for configuring the `Refresh rate` for the *Threads* and *Messages* APIs. 
> By default, the refresh rate for both APIs is **5 seconds**.

Simply open the file from the following path:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getThreadApiRefreshTimeHook()` method. Return the desired refresh rate.

```dart
@override
  ThreadApiRefreshTimeHook? getThreadApiRefreshTimeHook() {
    ThreadApiRefreshTimeHook? threadApiRefreshTimeHook = () {
      return 5;// time in seconds
    };

    return threadApiRefreshTimeHook;
  }
```

Similarly look for the `getMessageApiRefreshTimeHook()` method. Return the desired refresh rate.

```dart
@override
  MessageApiRefreshTimeHook? getMessageApiRefreshTimeHook() {
    MessageApiRefreshTimeHook? messageApiRefreshTimeHook = () {
      return 5;// time in seconds
    };

    return messageApiRefreshTimeHook;
  }
```


>  After modifications, restart the app and the changes will reflect in your app.

*Added in version 1.4.2*