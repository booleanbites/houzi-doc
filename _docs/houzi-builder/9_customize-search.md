---
title: Customize Search Filters
category: Houzi Builder
permalink: houzi-builder/customize_search_filters
order: 409
---

> **Important**: You are required to install the Houzi Rest Api Plugin on your Houzez wordpress. To install the Plug-in, click on [Houzi Rest Api Plugin Link](https://github.com/booleanbites/houzi-rest-api).

> A **Mobile App View** is provided in the center of screen, so you can see how the modifications will look on real device.  

<img src="../../images/search-screenshot.png" alt="search-screenshot" title="search-screenshot" border= "1px solid"/>  

> You can **Enable** *Cupertino Sliding Segment Control* instead of using Material Segment Control from [Api and Config](../houzi-builder/api_config_setup) section. 

This guide consists of following sections:

[Add New Section](#add-new-section)  
[Edit a Section](#edit-a-section)  
[Delete a Section](#delete-a-section)  
[Re-arrange a Section](#re-arrange-a-section)  

Let's dive into the details of each section.  

---  


# Add New Section 

There is a **Add** button at the bottom of the column. Press this button and a dialog box will open.  

  <img src="../../images/search-add-section-screenshot.png" alt="search-add-section-screenshot" title="search-add-section-screenshot" width= 300 border= "1px solid"/>  

You will encounter following fields on the dialog box:

[Widget Type](#widget-type)  
[Title](#title)  
[Data Type](#data-type)  
[Api Value](#api-value)  
[Picker Type](#picker-type)  
[Additional Fields](#additional-fields)  

### Widget Type:

You are provided with the dropdown list of  **Widget Types**. The details of widget types are as follows: 

* **term_picker:** If you want to search properties w.r.t. their
    - *Types* (e.g. apartment, office etc.)
    - *Status* (e.g. for-rent, for-sale etc.)
    - *Label* (e.g. hot-offer, open-house etc.)
    - *Features* (e.g. Air-Conditioning, Swimming-pool etc.)

* **location_picker:** If you want to search properties w.r.t. their
    - *City*
    - *Location*

* **range_picker:** If you want to search properties w.r.t. their
    - *Area*
    - *Price*

* **string_picker:** If you want to search properties w.r.t. specific attributes like
    - *Bedrooms*
    - *Bathrooms*
 
* **keyword_picker:** If you want to search properties w.r.t. some keywords e.g. Modern appartment with 2 bedrooms and 2 bathrooms etc.

* **custom_keyword_picker:** If you want to search properties w.r.t. some specified keywords.

* **keyword_custom_query_picker:** If you want to search properties w.r.t. some customized keyword query. You can define the *keyword* and send your custom query on its behalf.  

* **custom_field_picker:** If you want to search properties w.r.t. some custom field attributes. 

  <img src="../../images/search-widget-types-screenshot.png" alt="search-widget-types-screenshot" title="search-widget-types-screenshot" width= 300 border= "1px solid"/>   

  > **Custom Field Picker** depends upon the data of you website. If you have not defined any custom field, this picker would not available.  


### Title:

*Title* is label that will be displayed on the *Search Page. Define the **Title** of the section.


### Data Type:

You are provided with the dropdown list of **Data Types**. You can define the *Data Type* of the various sections as follows: 

* If selected *Widget Type* is **term_picker**, you can select from following data types:  

  - **property_type** (To search properties w.r.t. their type e.g. apartment, office etc.)

  - **property_status** (To search properties w.r.t. their status e.g. for-rent, for-sale etc.)

  - **property_feature** (To search properties w.r.t. their features e.g. Air-Conditioning, Swimming-pool etc.)

  - **property_label** (To search properties w.r.t. their Label e.g. hot-offer, open-house etc.)

  - **property_country** (To search properties w.r.t. Country)

  - **property_state** (To search properties w.r.t. States)

  - **property_city** (To search properties w.r.t. City)

  - **property_area** (To search properties w.r.t. Area)

    <img src="../../images/search-property-type-datatype-screenshot.png" alt="search-property-type-datatype-screenshot" title="search-property-type-datatype-screenshot" width= 300 border= "1px solid"/>

  > Above displayed **Data Types** are *generic houzez taxonomies*. You may encounter all or some of these options, according to the data of your website.

    
* If selected *Widget Type* is **range_picker**, you can select from following data types:  

  - **area** (To search properties within specific range of *area*)

  - **price** (To search properties within specific range of *price*)

    <img src="../../images/search-range-picker-area-datatype-screenshot.png" alt="search-range-picker-area-datatype-screenshot" title="search-range-picker-area-datatype-screenshot" width=300 border= "1px solid"/>  

* If selected *Widget Type* is **string_picker**, you can select from following data types:  

  - **bedrooms** (To search properties w.r.t. specific number of *bedrooms*)

  - **bathrooms** (To search properties w.r.t. specific number of *bathrooms*)

    <img src="../../images/search-string-picker-bedrooms-datatype-screenshot.png" alt="search-string-picker-bedrooms-datatype-screenshot" title="search-string-picker-bedrooms-datatype-screenshot" width=300 border= "1px solid"/>

> All the other *Widget Types* have *Default* Data Types. 

### Api Value:

Each section has its by default **Api Value**.


### Picker Type:

You are provided with the dropdown list of  **Picker Types**. The details of picker types are as follows: 


- If selected *Widget Type* is **term_picker**, you can select from following picker types:  

  - **tabs and chips:** To view properties related categories and sub-categories data in the form of *Tabs and Chips*.

  - **dropdown:** To view properties related categories and sub-categories data in the form of *Dropdown*.

  - **full_screen:** To view properties related categories and sub-categories data in the form of *full_screen* menu. A new page will open, listing all the property related catagories with additional *Search Bar* to search required catagory with ease.

  - **box:** To view properties related categories and sub-categories data in the form of *Grid View* having 3 catagories per row with their icons and titles.

    <img src="../../images/search-term-picker-pickertype-screenshot.png" alt="search-term-picker-pickertype-screenshot" title="search-term-picker-pickertype-screenshot" width=300 border= "1px solid"/>

  - If selected *Widget Type* is **string_picker**, you can select from following picker types:  

  - **chips:** To view properties related arrtibutes in the form of *Chips*.

  - **tabs:** To view properties related arrtibutes in the form of *Tabs*.

    <img src="../../images/search-string-picker-pickertype-screenshot.png" alt="search-string-picker-pickertype-screenshot" title="search-string-picker-pickertype-screenshot" width=300 border= "1px solid"/>

- If selected *Widget Type* is **custom_keyword_picker**, you can select from following picker types:  

  - **text_field:** To take *Keyword* input from the user.

  - **dropdown:** To provide users, a list of specified keywords in the form of *Dropdown Menu*.

  - **string_picker:** To provide users, specified keywords in the form of *Tabs* or *Chips*.

    <img src="../../images/search-custom-keyword-picker-pickertype-screenshot.png" alt="search-custom-keyword-picker-pickertype-screenshot" title="search-custom-keyword-picker-pickertype-screenshot" width=300 border= "1px solid"/>

- If selected *Widget Type* is **keyword_custom_query_picker**, you can select from following picker types:

  - **switch**

  - **checkbox**

    <img src="../../images/search-keyword-custom-query-picker-pickertype-screenshot.png" alt="search-keyword-custom-query-picker-pickertype-screenshot" title="search-keyword-custom-query-picker-pickertype-screenshot" width=300 border= "1px solid"/>

> All the other *Widget Types* have *Default* Picker Type. 

### Additional Fields

You can define some additional customizations for some sections. For this purpose you are provided with some **Additional fields**. Their details are as follows:


- If selected *Widget Type* is **location_picker**, you can set the value for the **Default Radius**. You can choose either to show **Search By City** or **Search By Location** or you can choose to show both.

  <img src="../../images/default-radius.png" alt="default-radius" title="default-radius" width= 300 border= "1px solid"/> 
  
  <img src="../../images/location-picker-additional-fields.png" alt="location-picker-additional-fields" title="location-picker-additional-fields" width= 300 border= "1px solid"/> 

- If selected *Widget Type* is **range_picker**, you can define the *minimun* and *maximun* range of section in **Min Value**, **Max Value** and **Steps** fields. 

    <img src="../../images/range-picker-additional-fields.png" alt="range-picker-additional-fields" title="range-picker-additional-fields" width= 300 border= "1px solid"/>  

- If selected *Widget Type* is **term_picker**, you can define the query type from dropdown menu in **Query Type** field. 

  - **OR Query Type:** If you want that search properties which may include this specific **term**, use *OR* query type.

  - **AND Query Type:** If you want that search properties which must include this specific **term**, use *AND* query type. 

      <img src="../../images/query-type-field-screenshot.png" alt="query-type-field-screenshot" title="query-type-field-screenshot" width= 300 border= "1px solid"/> 

      <img src="../../images/query-type-options-screenshot.png" alt="query-type-options-screenshot" title="query-type-options-screenshot" width= 300 border= "1px solid"/> 

- If selected *Widget Type* is **custom_keyword_picker**, you can define the **Unique key** and **Query Type**.  

    <img src="../../images/search-custom-keyword-picker-dialog.png" alt="search-custom-keyword-picker-dialog" title="search-custom-keyword-picker-dialog" width=300 height=600 border= "1px solid"/>

  - **Unique key** (Assign a unique key to this field e.g. *keyword-some-text*.)

  - **Query Type**: (Assign a query type to this field from the dropdown menu.) It has two following types:

    - **OR Query Type:** If you want that search properties which may include this specific keyword, use *OR* query type.

    - **AND Query Type:** If you want that search properties which must include this specific keyword, use *AND* query type.  

      <img src="../../images/query-type-field-screenshot.png" alt="query-type-field-screenshot" title="query-type-field-screenshot" width= 300 border= "1px solid"/> 

      <img src="../../images/query-type-options-screenshot.png" alt="query-type-options-screenshot" title="query-type-options-screenshot" width= 300 border= "1px solid"/> 

- If selected *Widget Type* is **custom_keyword_picker** and *Picker Type* is **dropdown** or **string_picker**. There are some additional fields as:

    - If the selecetd field is **dropdown** you can define your comma seperated specific keywords in **Options** field.  

      <img src="../../images/search-custom-keyword-picker-dialog-01.png" alt="search-custom-keyword-picker-dialog-01" title="search-custom-keyword-picker-dialog-01" width=300 border= "1px solid"/>  
      
    - If the selecetd field is **string_picker** you can define your comma seperated specific keywords in **Options** field. You can also specify *Sub-Picker Type* of *string_picker* i.e. *Chips* or *Tabs*.  

      <img src="../../images/search-custom-keyword-picker-dialog-02.png" alt="search-custom-keyword-picker-dialog-02" title="search-custom-keyword-picker-dialog-02" width=300 border= "1px solid"/>  

    - **Sub-Picker Types:**  

      <img src="../../images/search-custom-keyword-picker-dialog-03.png" alt="search-custom-keyword-picker-dialog-03" title="search-custom-keyword-picker-dialog-03" width=300 border="1px solid"/>  

  - If selected *Widget Type* is **keyword_custom_query_picker**, you can define the **Options**, **Unique key** and **Query Type**.  

    <img src="../../images/search-keyword-custom-query-picker-dialog.png" alt="search-keyword-custom-query-picker-dialog" title="search-keyword-custom-query-picker-dialog" width=300 height=650 border= "1px solid"/>  

  - **Options** (Define your comma seperated custom keyword query in this field.)

  - **Unique key** (Assign a unique key to this field e.g. *keyword-some-text*.)

  - **Query Type**: (Assign a query type to this field from the dropdown menu.) It has two following types:

    - **OR Query Type** If you want that search properties which may include this specific keyword, use *OR* query type.

    - **AND Query Type** If you want that search properties which must include this specific keyword, use *AND* query type.

      <img src="../../images/query-type-field-screenshot.png" alt="query-type-field-screenshot" title="query-type-field-screenshot" width= 300 border= "1px solid"/> 

      <img src="../../images/query-type-options-screenshot.png" alt="query-type-options-screenshot" title="query-type-options-screenshot" width= 300 border= "1px solid"/> 
    
> Click `Done` to *add* the new section.  
  Click `Cancel` to *discard* the action. 


---

## Edit a Section

You can **Edit** the sections just by clicking on **Edit Icon** of respective section. While editing a section, you can perform following actions:

- Modify section [Widget Type](#widget-type).
- Modify section [Title](#title).
- Modify section [Data Type](#data-type).
- Modify section [Api Value](#api-value).
- Modify section [Picker Type](#picker-type).
- Modify section [Additional Fields](#additional-fields).

---

## Delete a Section

You can **Delete** any section just by clicking on *delete icon* of respective section. A delete confirmation dialog will open.  

  <img src="../../images/search-list-tile-screenshot.png" alt="search-list-tile-screenshot" title="search-list-tile-screenshot" width=300 border= "1px solid"/>  

  <img src="../../images/search-delete-section-screenshot.png" alt="search-delete-section-screenshot" title="search-delete-section-screenshot" width=300 border= "1px solid"/>  
  
> Click **Delete** if you want to *delete* the section.  
  Click **Cancel** if you want to *discard* the action. 

---

## Re-arrange a Section

You can **Re-arrange** the sections on **Search Page**. Hold the section that you want to re-arrange and move it vertically (*upwards* or *downwards*). Place it on desire position in sections list.

<img src="../../images/search-re-arrange-01.png" alt="search-re-arrange-01" title="search-re-arrange-01" width= 400 border= "1px solid"/> 

<img src="../../images/search-re-arrange-02.png" alt="search-re-arrange-02" title="search-re-arrange-02" width= 400 border= "1px solid"/> 