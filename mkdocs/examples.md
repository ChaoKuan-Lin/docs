# Examples

In order to use MoBagel to effectively manage and analyze your devices, you will need address the two following questions about your product:

## What custom properties or events should I add to my report? 

Custom properties or events enables you to track anything that your hardware allows, such as temperature sensors, humidity sensors, accelerometers, feature usage, and status of components. To determine which custom properties to add, you should first list out all of the possible properties that your hardware is capable of tracking, and then ask yourself which of these properties would help your device management and analytics, such as which properties will lead to malfunctioning, or which properties will give you the customer insights that you want.

## How often should I send reports?

The frequency of sending reports varies according to the type of your product. It can range from once every few days to once every few seconds. If your product requires constant and careful monitoring, such as industrial machines or security systems, then you should send reports frequently in order to avoid delays in error detection. 

---
# Example: Smart Home

## Smart Air Conditioner

If you have a smart air conditioner, you might ask yourself these questions to help you decide which custom properties or events to track:


* What do I want to know about my users?

* How can I track these information?   

* How do they actually use your product?  

* What is the user's exact temperature preference over the course of a day/month/year?  

* Is the compressor functional?

* Is the ambient temperature abnormal?  

* Is the air conditioner actually saving the user on energy bills?


### Report basic device state with location

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

### Report custom device 

(including Device-ID, Mode, Temperature, Ambient-Temperature, Fan-Speed, Humidity, Power-Consumption, Power-Stability and Compressor-Status.)

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


## Smart Air Cleaner

If you have a smart air cleaner, you might ask yourself these questions to help you decide which custom properties or events to track:


* What do I want to know about my users?

* How can I track these information?   

* How do they actually use your product?  

* How often does the user use the product and under what conditions?

* How long do your air filters last?

* What season of the year do your customers use the air clean the most?

* What feature does the user love most about your product?

* What is the air quality of the user's room like? Could you possibly use this information to upsell more products?

### Report basic device state with location

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
### Report custom device  

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
# Example: Vending Machine

## Smart Vending Machine

Smart Vending Machine technology is evolving quickly, and new machines are engaging with customers like never before with touch-screen controls,  gesture-based interaction, and cashless payment. Unlike the past, vendors can now gain powerful insights about their vending machines and use them to maximize their business objectives. MoBagel can convert customer data to advanced inventory management and use predictive analytics to improve product forecasting. Through real-time monitor and predictive analytics, you can visualize and analyze your entire line of vending machines in a simple, easy-to-use dashboard.

Possible questions to ask yourself:

* What are the top factors that contribute to succcessful sales?

* What is your top selling product, and how many of them will be sold next month?

* How do I make the most efficient maintenance routes?

* Is the machine currently functional? When will the next malfunction be?

* How do your customers behave under different locations and times?


### Report basic device state with location

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

### Report custom device   

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