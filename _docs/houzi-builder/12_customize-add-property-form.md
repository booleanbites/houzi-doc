---
title: Customize Add Property Form
category: Houzi Builder
permalink: houzi-builder/customize_add_property_form
order: 411
---

> **Important**: You are required to install the Houzi Rest Api Plugin on your Houzez wordpress. To install the Plug-in, click on [Houzi Rest Api Plugin Link](https://github.com/booleanbites/houzi-rest-api).

> A **Mobile App View** is provided in the center of screen, so you can see how the modifications will look on real device.

<img src="../../images/add-property-screen.png" alt="add-property-screen" title="add-property-screen" border= "1px solid"/>

This guide consists of following sections.

[Add New Page](#add-new-page)  
This section guides through all the steps related to adding new Form Page.    

[Add New Section](#add-new-section)  
This section guides through all the steps related to adding new Form Section.    

[Add New Field](#add-new-field)  
This section guides through all the steps related to adding new Form Field.   

[Edit Page](#edit-page)  
This section guides through all the steps related to editing Form Page.    

[Edit Section](#edit-section)  
This section guides through all the steps related to editing Form Section.    

[Edit Field](#edit-field)  
This section guides through all the steps related to editing Form Field.  


# Add New Page  
You can `Add` a new Page in **Add Property Form** by following these steps:  

- Press the **Add Page** button at the right bottom of the screen, a dialog box will open.   

    <img src="../../images/add_new_page_dialog.png" alt="add-new-page-dialog" title="add-new-page-dialog" border= "1px solid"/>  
      
- The value of **Enable** field determines wether to *show/hide* the page. If you and to *show* the page, set the value to **true**. If you and to *hide* the page, set the value to **false**.

- Enter the **Title** of page.

- If you want to **restrict** this page to some specific users e.g. *administrator, houzez_agnecy etc.*, select these specific roles from the **Allowed Roles** multiselect dropdown menu. If you want to make the page **public** (available to all users), unselect all the roles (if any role is selected).

- Now [Add New Section/Sections](#add-new-section) in this page.

- Click **Done** button and a new page will be added in the **Add Property Form**.

- By clicking **Cancel** button, all changes will be discarded and page will not be added in the **Add Property Form**.

# Add New Section
You can `Add` a new Section in Page by following these steps:

- Press the **Add Section** button at the right bottom of the screen, a dialog box will open.   

    <img src="../../images/add_new_section_dialog.png" alt="add-new-section-dialog" title="add-new-section-dialog" border= "1px solid"/>  
      
- The value of **Enable** field determines wether to *show/hide* the section on page. If you and to *show* the section, set the value to **true**. If you and to *hide* the section, set the value to **false**.

- Enter the **Title** of section.

- Now [Add New Field/Fields](#add-new-field) in this section.

- Click **Done** button and a new section will be added in the page.

- By clicking **Cancel** button, all changes will be discarded and section will not be added in the page.

# Add New Field
You can `Add` a new Field in Section by following these steps: 

- Press the **Add Field** button at the right bottom of the screen, a dialog box will open.   

    <img src="../../images/add_new_field_dialog.png" alt="add-new-field-dialog" title="add-new-field-dialog" border= "1px solid"/>  
      
- The value of **Enable** field determines wether to *show/hide* the field on section. If you and to *show* the field, set the value to **true**. If you and to *hide* the field, set the value to **false**.

- If you want to make the input of any field **required**, set the value of **Make Field Required** as *true*. Similarly if you want to make the input of any field **optional**, set the value of **Make Field Required** as *false*.

- If you want to **restrict** this field to some specific users e.g. *administrator, houzez_agnecy etc.*, select these specific roles from the **Allowed Roles** multiselect dropdown menu. If you want to make the field **public** (available to all users), unselect all the roles (if any role is selected).

- **Field Type** is the type of *Form Widget* that you want to display on screen. e.g. Input Text Field, Dropdown etc. Select the desired *Form Widget Type* from **Field Type** dropdown.

    <img src="../../images/field_type_dropdown.png" alt="field-type-dropdown" title="field-type-dropdown" border= "1px solid"/> 

    The description of **Field Type** is as follows: 

    * **formTextField** should be used, if you want to take *text* input from user. e.g. Property Title, Property Price etc. You can define some assisting attributes like:

         <img src="../../images/form_text_field_options.png" alt="form-text-field-options" title="form-text-field-options" border= "1px solid"/>  
        
        * **Hint** is used as place holder for your field. e.g. *Enter property title* etc.

        * **Additional Hint** is used to provide extra assisting information about the field. e.g. additional hint of property price field: *Only digits* etc.

        * **Validation Types** are defined as follows:

            <img src="../../images/validation_type_options.png" alt="validation-type-options" title="validation-type-options" border= "1px solid"/> 

            * **String Validation** is used to check if the input is *non-empty*. Otherwise it will return error.

            * **Email Validation** is used to check if the entered input is properly *email-formatted*. Otherwise it will return error.

            * **Password Validation** is used to check if the entered input is properly *password-formatted*. Otherwise it will return error.

            * **Phone Number Validation** is used to check if the entered input is properly *phone-number-formatted*. Otherwise it will return error.

            * **User Name Validation** is used to check if the entered input is properly *user-name-formatted*. Otherwise it will return error.

        * **Max Lines** is used to define the max lines of field. If you want to show a *Text Area* for any property attribute e.g. Property Description, simply set the max lines to *5* or *7* as you desire.
        * **Keyboard Type** are defined as follows:

            <img src="../../images/keyboard_type_options.png" alt="keyboard-type-options" title="keyboard-type-options" border= "1px solid"/> 

            * **Text** is used to if you want to show normal keyboard for text input.

            * **Number** is used to if you want to show *Numeric* keyboard for text input.

            * **URL** is used to if you want to show *URL* assistive  keyboard for URL input.

            * **Email** is used to if you want to show *Email* assistive  keyboard for email input.

            * **MultiLine** is used to if you want to show text keyboard for *multi-line* input.

    * **formMultiSelectField** should be used, if you want to take *multiple* inputs from the user. e.g. Property Features (e.g. Garage, Pool etc.), Property Type (Commercail, Office etc.) etc.

    * **formDropDownField** should be used, if you want to take *single* inputs, from given list, from the user. e.g. Property Status (e.g. For Rent, For Sale etc.) etc.

    * **formStepperField** should be used, if you want to take such user input in which user can *increase* or *decrease* some value with the help of steppers. e.g. Number of bedrooms, Number of bathrooms etc.

    * **formMediaField** should be used, if you want to take media from user e.g. photos etc.

    * **formAdditionalDetailsField** should be used, if you want to take some *additional details/features* about property from user e.g. Equipment: Grill - Gas, Deposit: 20% etc.

    * **formCustomField** should be used, if you want to take user input in your custom defined Houzez fields.

- **[Required]** Enter the **Api Key** of field e.g. *fave_property_bedrooms etc.* The corresponding data of field will be sent to this key when **Add Property API** will be called.
    > *Note (In following cases, 'Authentic API key not required'):   
    > * Incase of **formMediaField** provide any key e.g. prop_media .
    > * Incase of **formCustomField** provide any key e.g. custom_field .

- **[Required]** Enter the **Title** of field.

- Enter the **Hint** of field. Hint is a placeholder for the empty field.

- Enter the **Additional Hint** of field. You can display some additional hint below the field, e.g. you can suggest the measuring unit of area as Sq. ft or m2 etc.

- Click **Done** button and a new field will be added in the section.

- By clicking **Cancel** button, all changes will be discarded and field will not be added in the section.

# Edit Page  

# Edit Section

# Edit Field
