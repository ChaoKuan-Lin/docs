# Vending Machine

## Smart Vending Machine
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