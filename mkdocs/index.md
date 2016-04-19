# Getting Started

---
# Introduction

MoBagel is an advanced device management and predictive analytics solution for hardware companies. Similar to Google Analytics or Mixpanel for web and mobile analytics, MoBagel is an analytics solution designed specifically for hardware devices. 

This short tutorial will outline the steps to integrate MoBagel with your devices and help you begin tracking your hardware usage today.

---
# Creating an account
If you do not have an account, please create an account [here](https://app.mobagel.com/signup). After you create an account, you will be directed to the dashboard.

---
# Creating a new product
To use MoBagel, you first have to create a `product`, which is essentially a group of same `device`. You will be prompted to create a new product when you first enter the dashboard.

After you create a `product`, you can go to Configuration -> Device Info to retrieve your `product_key`, which will be used to create `device` later on.

---
# Installing SDK on your device
MoBagel offers SDK in the following languages: 

* REST
* Java
* Node
* Swift
* Objective-C
* C++
* Python
* PHP


To find the detailed guide of a specific language, please click on 'Integrations' in the menu bar.

---
# Adding custom properties

In the Configuration, you can add custom properties to your product. Custom properties should have the following requirements:

* **ID**: Property ID (with the exception of `state`) should always begin with `c_` to indicate that it is a custom property. In addition, property IDs are unique and cannot repeat with itself.

* **Name**: The property name is your nickname for your property. For example, if your ID is 'c_012421', you can set the name as 'temperature'. The modules in the dashboard will display your property name instead of your property ID.

* **Type**: There are two types of properties: category and numeric. Category uses a set of string options and numeric uses numeric options (optional).

* **Options**:
    - **Category**: please add all the possible string values of your property by typing in the options column. The server will use this to prevent your devices from sending erroraneous reports.
    
    - **Numeric** (optional): please set a min and max value for your numeric property to help protect your data from errors. For example, if your numeric property is humidity level, then you can set min and max to 0 and 100, respectively. This will allow our system to reject any reports with humidity levels that are not in this range because those values are theoretically impossible (i.e. negative humidity level).

Please note that you must configure your properties in your configuration before you send your first customized report.



---
# Register your first device

Once you generated a `product_key` from the dashboard, you can use the `product_key` and `registerDevice` function to register a `device` in your application.

```

    // create mobagel object
    string product_key = "{YOUR_PRODUCT_KEY}";
    MoBagel *mobagel = new MoBagel(product_key);

    // register a device
    string device_key = mobagel->registerDevice();

```

---
# Sending first report

Once you connect the sensor properties, you can generate a report with the `sendReport` function.

```
    // sample report
    {
        "state": "normal",
        "c_humidity": 30,
        "c_function": "humidify" , 
        "c_temperature": 80 
    }

```
