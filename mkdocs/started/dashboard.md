# MoBagel Dashboard

----
# Introduction

Welcome to the **`MoBagel Dashboard`**, a snapshot of your devices for easy tracking and analysis.  

In this tutorial, we will guide you through each part of the MoBagel Dashboard.

----
# Your Current Products  

On the left hand side of the dashboard, under the MoBagel logo, a drop-down menu will list the products you have already created.  

<img src="../../../img/MoBagel_Dashboard/current_product-01.png" width="800">  

To create a new one, simply click on **`+New Product`**.    

<img src="../../../img/MoBagel_Dashboard/current_product_new_product.png" width="800">  

----
# The Dashboard

Listed below follows the order of the left menu on the MoBagel dashboard, skip to the page that most interests you or follow along and see what MoBagel's dashboard can do!

* Analytics
    * [Usage](#Usage)
    * [Segmentation](#Segmentation)
* Monitoring
    * Real Time
    * Notification
* Prediction
    * Calculate
    * Recommendations
* Configuration
    * Product Settings
    * Device Management
    * Data Setup
    * Docs

<a name="Usage"></a>  

----

## Analytics

* ###Usage 

    * `Usage` allows you to have a quick overview of all your devices all on one page, showing the number of users with regard to the time.

        <img src="../../../img/MoBagel_Dashboard/dashboard_overview.png" width="800">  
    
    * On the upper right hand side, click on `Day`, `Week`, `Month` or `Year` and the graph changes along with `Peak Usage` and `Lowest Usage` underneath.

        <img src="../../../img/MoBagel_Dashboard/dashboard_overview_day.png" width="800">

    >* `Total Users`
        * Shows all the current devices available
    >* `Active Users`
        * Shows devices currently active, this information can also be found in **_Configuration -> Device Management_**
    >* `Peak Usage`
        * Indicated at the highest point in the graph above.
    >* `Lowest Usage`
        * Indicated at the lowest point in the graph above.
 
    <img src="../../../img/MoBagel_Dashboard/dashboard_overview_bottom.png" width="800">

    * On the upper right hand side we will also find some useful tabs under Day, Week, Month, and Year for manipulating the user frequency graph.

        <img src="../../../img/MoBagel_Dashboard/Useful_tabs.png" width="200">
        <img src="../../../img/MoBagel_Dashboard/dashboard_zoom.png" width="800">

        ----
        * <img src="../../../img/MoBagel_Dashboard/useful_tabs_zoom.png" width="50"> - `Zoom`  
            * Choose a timeframe by clicking on Zoom once, then select the area on the graph you would like to magnify. Repeat to zoom in again.

        ----
        * <img src="../../../img/MoBagel_Dashboard/useful_tabs_reset.png" width="45"> - `Reset`
            * Graph goes back one step each time you click on Reset.
        
        ----
        * <img src="../../../img/MoBagel_Dashboard/useful_tabs_raw_data.png" width="45"> - `Raw Data`  
            * See Raw Data used to create the graph, click on “close” on the lower-right hand side to return to graph.
        
        ----
        * <img src="../../../img/MoBagel_Dashboard/useful_tabs_line.png" width="45"> - `Line`  
            * Line graph is set as default.

        ----
        * <img src="../../../img/MoBagel_Dashboard/useful_tabs_bar.png" width="45"> - `Bar`
            * Click on Bar to show data as a Bar graph.

        ----
        * <img src="../../../img/MoBagel_Dashboard/useful_tabs_save.png" width="45"> - `Save as Image`
            * Download current graph shown.  

    ----  
    * `Last Usage`  
        <img src="../../../img/MoBagel_Dashboard/Last_usage.gif" width="800">  

        * See how many reports were sent each hour for the last 24 hours. Place mouse cursor on bar for details.

    ----
    * `Last Usage Detail`
        <img src="../../../img/MoBagel_Dashboard/Last_usage_detail.png" width="800">
        * Time
            * Last time a report was sent.
        * Total Devices
        * Total Reports
        * See More In Segmentation
            * Click to filter customised results in the “Segmentation” page.  

    ----  
    * `Property Breakdown`
        <img src="../../../img/MoBagel_Dashboard/property_breakdown.png" width="800">
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



* ###Segmentation
    * `Condition`  
        
        ----
        * Create a segment using filters, for a specific timeframe or property states
        <img src="../../../img/MoBagel_Dashboard/Segmentation_none.gif" width="800">
        ----
        * Click on `Add rule` on the right hand side
        <img src="../../../img/MoBagel_Dashboard/Segmentation_condition.png" width="800">
        ----
        * Click on `Add group` for more complex filtering
        * Select the properties you would like to filter with `AND` / `OR`.
        <img src="../../../img/MoBagel_Dashboard/Segmentation_final.png" width="800">
        
        * e.g. "state equal normal" `AND` "temperature_C is greater than 30” `AND` ("light_pct is null" `OR` “period_s is not null”)
    
    ----
    * `Series`
        
        ----
        * Analyse the segment by comparing different series.
        <img src="../../../img/MoBagel_Dashboard/segmentation_series_1.png" width="800">
        ---- 
        * Click `+Add` to create a new series.
        <img src="../../../img/MoBagel_Dashboard/segmentation_series_2.png" width="800">
        ----
        * Add as many series you would like to compare.
        <img src="../../../img/MoBagel_Dashboard/segmentation_series_3.png" width="800">
        * e.g. We would like to see the a series that shows “state equal normal” and compare this to another series “temperature_C greater 33” on the same graph
    
    ----
    * `Select Y-Axis`
        
        ----
        * Configure your result to display the number of devices, number of reports, or property with respect to time.
        <img src="../../../img/MoBagel_Dashboard/select_y_1.png" width="800">
        
        ----
        * e.g. Here we choose `Device`.
        <img src="../../../img/MoBagel_Dashboard/select_y_2.png" width="800">
    

    ----
    * `Select Chart Type`
        
        ----
        * Line graph is set as default.
        <img src="../../../img/MoBagel_Dashboard/select_chart_type.png" width="800">  
    
    ----    
    * `Result`
        
        ----
        * Scroll to the bottom of the page to generate results.
        <img src="../../../img/MoBagel_Dashboard/result_0.png" width="800">  
        ----
        * Set the time frame on the right hand side
        <img src="../../../img/MoBagel_Dashboard/result_dates.png" width="800"> 
        ----
        * e.g. 12/01/2015 - 12/03/2016
        <img src="../../../img/MoBagel_Dashboard/result_dates_custom.png" width="800"> 
        ----
        * Click `Generate`, this will need to be done every time there are changes made to the filters above.
        <img src="../../../img/MoBagel_Dashboard/result_generate.gif" width="800"> 
        ----
        * Click on the name of the series to hide/show it on the graph.
        <img src="../../../img/MoBagel_Dashboard/result_result_hide.gif" width="800"> 
        ----
        * `Zoom`, `Reset`, `Raw Data`, `Line`, `Bar` and `Save as Image` work the same way as mentioned before.

<!---
----
## Monitoring

* Real Time
* Notification

----
## Prediction

* Calculate
* Recommendations

----
## Configuration

* Product Settings
    * Device Settings 
    * Report Settings 
    * Delete Product
* Device Management
    * Device Summary 
    * Device List 
* Data Setup
    * Register Sample Device 
    * Send Sample Report 
* Docs
