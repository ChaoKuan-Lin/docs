# Smart Home

## Smart Air Conditioner

Smart Air Conditioner has the brains to minimize energy usage without sacrificing comfort. With a host of automation features, it improves user experience and enhance convenience. 

### What report needs?
So what kind of information should you include in the report?  
In other words, what do you want to know from users?   
How do they actually use your product?  
What exact temperature does the user prefer?  
Is the compressor working alright?  
Is the ambient temperature abnormal?  
Wants to learn user’s weekly time table and preference to turn on the air-conditioner?  
Or maybe in a complicated scenario, whether people turned their air conditioners off when they left home to save money and conserve energy or left them on to ensure that their home was cool and comfortable when they returned?  

Every report will contain rich metadata according to your custom settings. You can easily monitor and manage your devices on MoBagel's dashboard. Moreover, with real-time predictive analytics, preventing errors is also the main function of our service. 

### Frequency of sending report?
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


## Smart Lock


## Smart Air Cleaner

## Smart Robot Cleaner

## Smart TV