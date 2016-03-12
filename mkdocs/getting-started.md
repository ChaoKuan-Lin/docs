# Getting Started

---
## Introduction

MoBagel is an advanced device management and predictive analytics solution for hardware companies. Similar to Google Analytics or Mixpanel for web and mobile analytics, MoBagel is an analytics solution designed specifically for hardware devices. 

This short tutorial will outline the steps to integrate MoBagel with your devices and help you begin tracking your hardware usage today.

---
## Creating an account
If you do not have an account, please create an account [here](https://app.mobagel.com/signup). After you create an account, you will be directed to the dashboard.

---
## Creating a new product
To use MoBagel, you first have to create a `product`, which is essentially a group of same `device`. You can create new products in the dashboard. 

For example:     

 * [Product Name] iBulb
 * [Product Brief] Smart light bulb
 * [Product Description] Wi-Fi connected light bulb with motion sensors and temperature sensors.

After you create a `product`, the system will generate a `product_key`, which will be used to create `device` later on.

---
## Installing SDK on your device
MoBagel offers SDK in the following languages: 

* REST
* Java
* NodeJS
* Objective-C
* C/C++
* Python
* PHP


To find the detailed guide of a specific language, please click on 'Integrations' in the menu bar.

---
## Register your first device

Once you generated a `product_key` from the dashboard, you can use the `product_key` and `registerDevice` function to register a `device` in your application.

```

    // create mobagel object
    string product_key = "1111111111222222222233333333334444444444555555555566666666667777";
    MoBagel *mobagel = new MoBagel(product_key);

    // register a device
    string device_key = mobagel->registerDevice();

```

---
## Connecting sensor properties






---
## Sending first report

Once you connect the sensor properties, you can generate a report with the `sendReport` function.

```
    // sample report
    "data":
    {
        "state": "normal",
        "c_humidity": 30,
        "c_function": "humidify" , 
        "c_temperature": 80 
    }

```
