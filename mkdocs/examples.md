# Examples

In order to effectively use MoBagel to manage and analyze your devices, you will need address the two following questions about your product:

1. What custom properties should I add to my report? 

2. How often should I sent reports?

---
## Smart Home

### Smart Air Conditioner

![airconditioner](../../img/docs/airconditioner.png)

Smart Air Conditioner has the brains to minimize energy usage without sacrificing comfort. With a host of automation features, it improves user experience and enhance convenience. 

#### What report needs?
So what kind of information should you include in the report?  
In other words, what do you want to know from users?   
How do they actually use your product?  
What exact temperature does the user prefer?  
Is the compressor working alright?  
Is the ambient temperature abnormal?  
Wants to learn user’s weekly time table and preference to turn on the air-conditioner?  
Or maybe in a complicated scenario, whether people turned their air conditioners off when they left home to save money and conserve energy or left them on to ensure that their home was cool and comfortable when they returned?  

Every report will contain rich metadata according to your custom settings. You can easily monitor and manage your devices on MoBagel's dashboard. Moreover, with real-time predictive analytics, preventing errors is also the main function of our service. 

#### Frequency of sending report?
According to different products, you can set the frequency of sending report.  
As to Smart Air Conditioner, our default value will be 1 minute.
Every minute, the Smart Air Conditioner will send a report up to the cloud.


Example: Report basic device state with location
```http
POST /products/A001/devices/D001/reports

{
    "data":
    {
        "state": "Normal",
        "latitude": 12.321,
        "longitude": -32.12
    }
}
```
Example: Report custom device   
(Including Device-ID, Mode, Temperature, Ambient-Temperature, Fan-Speed, Humidity, Power-Consumption, Power-Stability and Compressor-Status.)

```http
POST /products/A001/devices/D001/reports

{
    "data":
    {
        "state": "Normal",
        "c_id": 5512,
        "c_mode": "cooling",
        "c_temperature": 23.5,
        "c_t-unit": "°C",
        "c_ambient_temp": 27,
        "c_at-unit": "°C",
        "c_speed": "Low",
        "c_humidity": 58,
        "c_h-unit": "%",
        "c_power-consum": 2.0,
        "c_p-unit": "kW",
        "c_power-stable": "normal",
        "c_compressor": "normal"

    }
}
```


### Smart Air Cleaner

Smart Air Cleaner can see the air and keep harmful particles outdoor initiatively. It works behind the scenes to help users breathe cleaner, fresher air in their home.   
What enhances purchasing intent?   
It's the automatic detection and intelligent functions. Your product can keep consumers as comfortable as possible while saving them money and providing them a cleaner environment.  
With MoBagel device management service, you can easily visualize problems and advance user experience. 

#### What report needs?
How to get a useful report instead of unorganized, messy information?  
First, you'll have to decide what you want to know from the users.  
Such as how do users actually use your product,  
when does the user turn on/off,  
which speed mode does the user prefer,  
How's the air quality?  
Moreover, you can visualise user's bedtime through switching the mode to night mode.  
Is the fan running normally or too much fluff sticking to it?  
You might also want to know about  the status of the filter, in order to proactively sell new filters to the user. 
  

Every report will contain rich metadata according to your custom settings. You can easily monitor and manage your devices on MoBagel's dashboard. Moreover, with real-time predictive analytics, preventing errors is also the main function of our service.

#### Frequency of sending report?
According to different products, you can set the frequency of sending report.  
As to Smart Air Cleaner, our default value will be 5 minutes.
Every 5 minutes, the Smart Air Cleaner will send a report up to the cloud.

Example: Report basic device state with location
```http
POST /products/A002/devices/D001/reports

{
    "data":
    {
        "state": "Normal",
        "latitude": 14.174,
        "longitude": -72.17
    }
}
```
Example: Report custom device   
(Including Device-ID, Mode, Speeed, Air-Quality, Fan-Status, Compressor-Status, Filter-Usage.)

```http
POST /products/A002/devices/D001/reports

{
    "data":
    {
        "state": "Normal",
        "c_id": 1612,
        "c_mode": "night mode",
        "c_speed": "high",
        "c_air-quality": 2.7,
        "c_air-unit": "PM",
        "c_fan-status": "Normal",
        "c_compressor": "Normal"
        "c_filter-usage": 76,
        "c_filter-unit": "%",

    }
}
```

---
## Vending Machine

### Smart Vending Machine
![vending machine](../../img/docs/vending.png)

Smart Vending Machine technology is evolving quickly, and new machines are engaging shoppers like never before with touch-screen controls,  gesture-based interaction, and cashless payment. Unlike the past, more and more information are collected. MoBagel can analyze all these customer data to advance inventory management and improve product forecasting. Through real-time monitor and predictive analytics, you can also visualize your vending machine status on MoBagel dashboard and make sure everything is alright.

### What report needs?
What kind of useful information should you include in the report?    
In other words, what do you want to know from the shoppers and the machines?    
Is the machine temperature normal,  
Is there enough coins,  
What kind of products and how many of them are sold in a period of time.  
We can also collect information from the customers.   
Such as the gender/age/emotion of the customers.  
What kind of customers buy what type of products?  
Does the weather influence specific product sales number?  

Every report will contain rich metadata according to your custom settings. You can easily monitor and manage your devices on MoBagel's dashboard. With real-time predictive analytics, preventing errors is also the main function of our service.

### Frequency of sending report?
According to different products, you can set the frequency of sending report.    
As to Smart Vending Machine, our default value will be 10 minutes.  
Every 10 minutes, the Smart Vending Machine will send a report up to the cloud.

Example: Report basic device state with location
```http
POST /products/A003/devices/D001/reports

{
    "data":
    {
        "state": "Normal",
        "latitude": 15.175,
        "longitude": -73.14
    }
}

```
Example: Report custom device   
(Including Device-ID, Mode, Speeed, Air-Quality, Fan-Status, Compressor-Status, Filter-Usage.)

```json
POST /products/A003/devices/D001/reports

{
    "data":
    {
        "state": "Normal",
        "c_id": 3456,
        "c_temperature": 8,
        "c_temp-unit": "°C",
        "c_coin": 47,
        "c_coin-unit": "%",
        "c_product_1": 1,
        "c_p1-unit": "times",
        "c_product_2": 3,
        "c_p2-unit": "times",
        "c_product_6": 1,
        "c_p6-unit": "times",
        "c_female": 2,
        "c_male": 3,
        "c_age-10~15": 0,
        "c_age-15~25": 1,
        "c_age-25~35": 0,
        "c_age-35~45": 3,
        "c_age-35~45": 1,
        "c_age-45~55": 0,
        "c_ambient-tem": 28,
        "c_ambient-unit": "°C",
    }
}
```