---
title: Direct Messages
category: Tools Setup
permalink: tools/direct_messages
order: 24
---

Direct Messages is one of the best way to contact the realtor. We’ve incorporated this feature to enhance engagement between clients and realtors. 

To use the Direct Message feature, you will need to perform some configurations on your WordPress site. 

This guide includes the following sections:

- [Direct Messages Setup on WordPress](#direct-messages-setup-on-wordpress)
    - [1. Enable Direct Message Button:](#1-enable-direct-message-button)
    - [2. Create Message Page:](#2-create-message-page)
    - [3. Edit Houzez Theme File: ](#3-edit-houzez-theme-file)
- [Houzi Package via Houzi Builder](#houzi-package-via-houzi-builder)
- [Direct Messages Configuration via Hooks](#direct-messages-configuration-via-hooks)


## Direct Messages Setup on WordPress

You have to provide these following configurations:

### 1. Enable Direct Message Button:

Go to the `Theme Options > Contact Forms`.  Enable the *Direct Message Button* setting and Save Changes.

<img src="../../images/messages-setup-wordpress-01.png" alt="messages-setup-wordpress-01" title="messages-setup-wordpress-01" border="1px solid"/>  

### 2. Create Message Page:

- Go to the `Pages` and click on `Add New`.  
- Set title as **Messages**. 
- Click on **Default template** and select *User Dashboard Messages* from the dropdown.
- Click the **Publish** button.

<img src="../../images/messages-setup-wordpress-02.png" alt="messages-setup-wordpress-02" title="messages-setup-wordpress-02" border="1px solid"/>  

### 3. Edit Houzez Theme File:

- Go to the **Theme File Editor** (path: `Appearance > Theme File Editor`).
- Select the **Houzez** theme from the dropdown and click the *Select* button.
- Go to the **emails-function.php** (path: `framework > functions > emails-function.php`). 
- Find the function `houzez_send_messages_emails`.
- Add these lines just before **@wp_mail**.
- Click the **Update File** button.

```php
$notificationArgs = array(
            "title" => $subject,
            "message" => $message,
            "type" => "messages",
            "to" => $user_email,
        );

do_action('houzez_send_notification', $notificationArgs);
```

<img src="../../images/messages-setup-wordpress-03.png" alt="messages-setup-wordpress-03" title="messages-setup-wordpress-03" border="1px solid"/>  


## Houzi Package via Houzi Builder

- Go to the **Property Profile** section of the Houzi Builder and enable/disable the *Direct Message* button. Checkout HouziBuilder [Property Profile Configurations](/houzi-builder/customize_property_profile#property-profile-configurations). 

- Go to the **Navigation Bar** section of the Houzi Builder and configure the *Direct Messages*. Checkout HouziBuilder [Navigation Bar Configurations](/houzi-builder/customize_navigation_bar#add-new-section). 

## Direct Messages Configuration via Hooks

Checkout [Direct Messages Hooks](/hooks-widgets/direct_messages_hooks) for further direct messages configurations. 



>  **❗️❗️IMPORTANT❗️❗️**
>
>  [Direct Messages Setup on WordPress](#direct-messages-setup-on-wordpress) is required. Please ensure that you have configured Direct Messages on your Wordpress before configuring via **HouziBuilder** and **Hooks**.

 *Added in version 1.4.2*