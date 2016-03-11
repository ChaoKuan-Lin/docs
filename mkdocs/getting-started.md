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
To use MoBagel, you first have to create a `product`, which is essentially a group of same `devices`. You can create new products in the dashboard. 

For example:     

 * [Product Name] iBulb
 * [Product Brief] Smart light bulb
 * [Product Description] Wi-Fi connected light bulb with motion sensors and temperature sensors.

After you create a `product`, you will receive a `product_key`, which will be used to create `devices` later on.

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
## Connecting sensor properties



---
## Creating device


---
## Sending first report

To send a report, there are little steps to do:

1. Prepare your Device Key
2. 


\\
 

    Assume that your device id is `D001`.

    To get your device information, your sample request will be:

    + Host: `https://api.mobagel.com/products/A001/devices/D001/reports`
    + Header: 

            Device-Id: D001

    + Body:

            {
                "data":
                {
                    "state": "normal",
                    "latitude": 12.321, 
                    "longitude": -32.12 
                }
            }

    *For more information about body, please see [introduction](user-guide/introduction.md)*

    You will receive a sample response like this:

        HTTP/1.1 201 CREATED
        Date: Mon, 26 Oct 2015 07:48:06 GMT
        Content-Length: 81
        Connection: keep-alive
        Content-Type: application/json
        Server: nginx/1.4.6 (Ubuntu)

        {
            "code": 201,
            "message": "success",
            "data": "$reportId"
        }

    > *You can send your sample request [here](https://apigee.com/console/others)*


