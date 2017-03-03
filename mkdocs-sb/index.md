# MoBagel Dashboard

----
## Introduction

Welcome to the **`MoBagel Dashboard`**, a snapshot of your devices for easy tracking and analysis.  

In this tutorial, we will guide you through how to upload data to the MoBagel Dashboard.


----
## Uploading your data  

With the `MoBagel data uploading tool`, you can easily upload your .csv data to process on the MoBagel Dashboard.

---

Type in a name for your product.    
<img src="../img/SB_Dashboard/1.png" width="800"> 

---
Click on continue.    
<img src="../img/SB_Dashboard/2.png" width="800"> 

---
Find the `Product Key` under Product Settings.    
<img src="../img/SB_Dashboard/3.png" width="800"> 

---
Set up your `Report Settings` under Product settings.    
<img src="../img/SB_Dashboard/4.png" width="800"> 

---
Copy the `Product Key`.    
<img src="../img/SB_Dashboard/5.png" width="800"> 

---
Open the MoBagel data uploading tool.    
<img src="../img/SB_Dashboard/6.png" width="800"> 

---
Find the .csv file you would to upload.    
<img src="../img/SB_Dashboard/7.png" width="800"> 

---
Here you can see what your data looks like.    
<img src="../img/SB_Dashboard/8.png" width="800"> 

---
Here you can see all the data types of your data.    
<img src="../img/SB_Dashboard/9.png" width="800">

---
You will need to come here and Copy the `Product Key` if you haven't yet.     
<img src="../img/SB_Dashboard/10.png" width="800"> 

---
On the third tab `Analyze` you will find a place to fill in the `Product Key`.    
<img src="../img/SB_Dashboard/11.png" width="800"> 

---
Paste the `Product Key`.    
<img src="../img/SB_Dashboard/12.png" width="800"> 

---
Click on Submit and upload.    
<img src="../img/SB_Dashboard/13.png" width="800"> 

---
Return to the dashboard and find your new device under `Device Management`.    
<img src="../img/SB_Dashboard/14.png" width="800"> 

---
Click on the device and you will find that all your data has been uploaded.    
<img src="../img/SB_Dashboard/15.png" width="800"> 

---

----
## Your Current Products  

On the left hand side of the dashboard, under the MoBagel logo, a drop-down menu will list the products you have already created.  

<img src="../img/MoBagel_Dashboard/current_product-01.png" width="800">  

To create a new one, simply click on **`+New Product`**.    

<img src="../img/MoBagel_Dashboard/current_product_new_product.png" width="800">  

----
# The Dashboard

Listed below follows the order of the left menu on the MoBagel dashboard, skip to the page that most interests you or follow along and see what MoBagel's dashboard can do!

* Analytics
    + [Usage](#Usage)
* Monitoring
    + [Real Time](#Real_Time)
    + [Notification](#Notification)
* Prediction
    + [Recommendations](#Recommendations)

<a name="Usage"></a>  

----

## Analytics

### Usage 

* `Usage` allows you to have a quick overview of all your devices all on one page, showing the number of users with regard to the time.

    <img src="../img/MoBagel_Dashboard/dashboard_overview.png" width="800">  

* On the upper right hand side, click on `Day`, `Week`, `Month` or `Year` and the graph changes along with `Peak Usage` and `Lowest Usage` underneath.

    <img src="../img/MoBagel_Dashboard/dashboard_overview_day.png" width="800">

>* `Total Users`
    * Shows all the current devices available
>* `Active Users`
    * Shows devices currently active, this information can also be found in **_Configuration -> Device Management_**
>* `Peak Usage`
    * Indicated at the highest point in the graph above.
>* `Lowest Usage`
    * Indicated at the lowest point in the graph above.

<img src="../img/MoBagel_Dashboard/dashboard_overview_bottom.png" width="800">

* On the upper right hand side we will also find some useful tabs under Day, Week, Month, and Year for manipulating the user frequency graph.

    <img src="../img/MoBagel_Dashboard/Useful_tabs.png" width="200">
    <img src="../img/MoBagel_Dashboard/dashboard_zoom.png" width="800">

    ----
    * <img src="../img/MoBagel_Dashboard/useful_tabs_zoom.png" width="50"> - `Zoom`  
        * Choose a timeframe by clicking on Zoom once, then select the area on the graph you would like to magnify. Repeat to zoom in again.

    ----
    * <img src="../img/MoBagel_Dashboard/useful_tabs_reset.png" width="45"> - `Reset`
        * Graph goes back one step each time you click on Reset.
    
    ----
    * <img src="../img/MoBagel_Dashboard/useful_tabs_raw_data.png" width="45"> - `Raw Data`  
        * See Raw Data used to create the graph, click on “close” on the lower-right hand side to return to graph.
    
    ----
    * <img src="../img/MoBagel_Dashboard/useful_tabs_line.png" width="45"> - `Line`  
        * Line graph is set as default.

    ----
    * <img src="../img/MoBagel_Dashboard/useful_tabs_bar.png" width="45"> - `Bar`
        * Click on Bar to show data as a Bar graph.

    ----
    * <img src="../img/MoBagel_Dashboard/useful_tabs_save.png" width="45"> - `Save as Image`
        * Download current graph shown.  

----  
* `Last Usage`  
    <img src="../img/MoBagel_Dashboard/Last_usage.gif" width="800">  

    * See how many reports were sent each hour for the last 24 hours. Place mouse cursor on bar for details.

----
* `Last Usage Detail`
    <img src="../img/MoBagel_Dashboard/Last_usage_detail.png" width="800">
    * Time
        * Last time a report was sent.
    * Total Devices
    * Total Reports
    * See More In Segmentation
        * Click to filter customised results in the “Segmentation” page.  

----  
* `Property Breakdown`
    <img src="../img/MoBagel_Dashboard/property_breakdown.png" width="800">
    * Listed here are all sensor properties sent in each report, also showing the range of values for each property.
        * Numeric Property
        * Category Property

----
* `Usage Location`
    * Manage your devices and see where they are located from latitude and longitude data in the report.
        * Country
        * User
        * %User

<a name="Segmentation"></a>  

----

### Segmentation
* `Condition`  
    
    ----
    * Create a segment using filters, for a specific timeframe or property states
    <img src="../img/MoBagel_Dashboard/Segmentation_none.gif" width="800">
    ----
    * Click on `Add rule` on the right hand side
    <img src="../img/MoBagel_Dashboard/Segmentation_condition.png" width="800">
    ----
    * Click on `Add group` for more complex filtering
    * Select the properties you would like to filter with `AND` / `OR`.
    <img src="../img/MoBagel_Dashboard/Segmentation_final.png" width="800">
    
    * e.g. "state equal normal" `AND` "temperature_C is greater than 30” `AND` ("light_pct is null" `OR` “period_s is not null”)

----
* `Series`
    
    ----
    * Analyse the segment by comparing different series.
    <img src="../img/MoBagel_Dashboard/segmentation_series_1.png" width="800">
    ---- 
    * Click `+Add` to create a new series.
    <img src="../img/MoBagel_Dashboard/segmentation_series_2.png" width="800">
    ----
    * Add as many series you would like to compare.
    <img src="../img/MoBagel_Dashboard/segmentation_series_3.png" width="800">
    * e.g. We would like to see the a series that shows “state equal normal” and compare this to another series “temperature_C greater 33” on the same graph

----
* `Select Y-Axis`
    
    ----
    * Configure your result to display the number of devices, number of reports, or property with respect to time.
    <img src="../img/MoBagel_Dashboard/select_y_1.png" width="800">
    
    ----
    * e.g. Here we choose `Device`.
    <img src="../img/MoBagel_Dashboard/select_y_2.png" width="800">


----
* `Select Chart Type`
    
    ----
    * Line graph is set as default.
    <img src="../img/MoBagel_Dashboard/select_chart_type.png" width="800">  

----    
* `Result`
    
    ----
    * Scroll to the bottom of the page to generate results.
    <img src="../img/MoBagel_Dashboard/result_0.png" width="800">  
    ----
    * Set the time frame on the right hand side
    <img src="../img/MoBagel_Dashboard/result_dates.png" width="800"> 
    ----
    * e.g. 12/01/2015 - 12/03/2016
    <img src="../img/MoBagel_Dashboard/result_dates_custom.png" width="800"> 
    ----
    * Click `Generate`, this will need to be done every time there are changes made to the filters above.
    <img src="../img/MoBagel_Dashboard/result_generate.gif" width="800"> 
    ----
    * Click on the name of the series to hide/show it on the graph.
    <img src="../img/MoBagel_Dashboard/result_result_hide.gif" width="800"> 
    ----
    * `Zoom`, `Reset`, `Raw Data`, `Line`, `Bar` and `Save as Image` work the same way as mentioned before.

<a name="Real_Time"></a>  

----
## Monitoring

### Real Time

* If you have not set up any monitoring or alerts, click on the blue `Set up now` button. You will then be taken to the `Notification` page.
* Continue this part after you have configured your settings in `Notificaiton`.
    <img src="../img/MoBagel_Dashboard/Real_time_set_up.png" width="800"> 
* All changes from your device reports will show on screen in real time, coming from the right.
    <img src="../img/MoBagel_Dashboard/Real_Time.gif" width="800">

<a name="Notification"></a>  

----
### Notification
* Click on `Configure Notification` to set up monitoring for your product. 
<img src="../img/MoBagel_Dashboard/Notifications_start.png" width="800">


* Current Notification Method
    - Your currnet method of notification is shown here.
    <img src="../img/MoBagel_Dashboard/Notifications_empty_1.png" width="800">

* Configure Method
    - Your currnet method of notification is shown here.
    <img src="../img/MoBagel_Dashboard/Notifications_empty_2.png" width="800">

* Configure Normal Ranges
    * If you have not set up `Device Settings` you will find nothing here.
    <img src="../img/MoBagel_Dashboard/Notifications_empty_000.png" width="800">
    * Configure your normal ranges here by clicking on the `Edit` button. If your report values exceed the ranges, you will receive a notification.
    <img src="../img/MoBagel_Dashboard/Configure_Normal_Ranges.gif" width="800">

<a name="Recommendations"></a>      

----
## Prediction

### Recommendations

----    
* On the top of the page, you can decide the frequency of the data and the time window you would like to observerve.
<img src="../img/MoBagel_Dashboard/Recommendations_none.gif" width="800">
    
    ----
    * The `History`(Red Line) and `Prediction`(Dotted Line) of your report data will be shown here.
    <img src="../img/MoBagel_Dashboard/Recommendations_all.png" width="800">
    ----
    * Click on `Prediction` to hide `Prediction`.
    <img src="../img/MoBagel_Dashboard/Recommendations_hide_prediction.png" width="800"> 
    ----
    * Click on `History` to hide `History`.
    <img src="../img/MoBagel_Dashboard/Recommendations_hide_history.png" width="800">
    ----
    * Suggestions for various actions will be listed on the right hand side.
    <img src="../img/MoBagel_Dashboard/Recommendations_suggestions.png" width="800">
