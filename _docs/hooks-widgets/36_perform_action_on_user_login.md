---
title: Perform Action on User Login
category: Hooks & Widgets
permalink: hooks-widgets/perform_action_on_user_login
order: 336
---

Houzi proivdes you with the **getUserLoginActionHook()**  to perform some action on User Login.  Simply open the file from the following path:

`Project_HOME  > lib > hooks_v2.dart`

Look for the `getUserLoginActionHook()` method.

```dart
@override
  UserLoginActionHook? getUserLoginActionHook() {
    UserLoginActionHook loginActionHook = ({
      required context,
      required formKey,
      required usernameEmail,
      required password,
      required loginNonce,
      required defaultLoginFunc}) {
      // define your action here
    };

    // return loginActionHook;
    return null;
  }
```

You are provided with the following parameter:

- [context](#context)  
- [formKey](#formkey)  
- [usernameEmail](#usernameemail)  
- [password](#password)  
- [loginNonce](#loginnonce)  
- [defaultLoginFunc](#defaultloginfunc)  

Let's dive into the details of each parameter.

## context

context is the Build Context. You are provided with the context so you can perform build context related actions.

## formKey

You are provided with the formKey so could perform form actions. e.g. you can validate the form fields using the formKey etc.

For validating the form state just type following code:

```dart
formKey.currentState!.validate();
```

## usernameEmail

After validating the form fields, you can save the form state and then you will get the input provided by the user as Email or User name in the usernameEmail parameter.

For saving the form state just type following code:

```dart
formKey.currentState!.save();
```

## password

After validating the form fields, you can save the form state and then you will get the input provided by the user as password in the password parameter.

For saving the form state just type following code:

```dart
formKey.currentState!.save();
```

## loginNonce

You are required to pass a login nonce along the user credientials for the user login. You are provided with the loginNonce for this purpose.

## defaultLoginFunc

If you want to perform some additional actions along the default Houzi Login Action, you can use the defaultLoginFunc for this purpose.
Just define your additional actions and at the end use the defaultLoginFunc.

For example:

```dart
UserLoginActionHook loginActionHook = ({
      required context,
      required formKey,
      required usernameEmail,
      required password,
      required loginNonce,
      required defaultLoginFunc}) {
      // define your actions here
      actions();
      // use defaultLoginFunc at the end
      defaultLoginFunc();
    };
  ```

>  - Return `loginActionHook` instead of null for the modifications to work. 

```dart
@override
  UserLoginActionHook? getUserLoginActionHook() {
    UserLoginActionHook loginActionHook = ({
      required context,
      required formKey,
      required usernameEmail,
      required password,
      required loginNonce,
      required defaultLoginFunc}) {
      // define your action here
    };

     return loginActionHook;
  }
```

> - After modifications, restart the app and the changes will reflect in your app.