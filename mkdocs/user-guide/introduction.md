# Introduction

This section covers the basics of the MoBagel API and how you can utilize MoBagel's platform to improve your IoT devices.


---

## Request
To access the MoBagel API, you first have to set up http headers. Add the following headers to your requests:

+ product_id
+ device_id

If you use `POST` method, the Content-Type must be `application/json`, and the post data should follow the format below:

    {
        "data": {
            "field": "value"
        }
    }

**Note:** field will be defined by each API

## Response
For each response, the format will look like:

    {
        "code": $code,
        "message": $message,
        "timestamp": $timestamp,
        "data": $data
    }

*More information about [error handling](error-handling.md)*

## Report API
According to different products, you can set the frequency of report sending.  
For example, you set the frequency : 30 seconds  
Every 30 seconds, your device will send a report to the cloud.

![report](../../img/docs/report.png)

Method: `POST`

Path: `/products/{product_id}/devices/{device_id}/reports`

| Parameter        | Type          | Description                       |
| :--:             | :-----:       | :----                             |
| state            | string        | State of device                   |
| latlng(optional) | string        | Latitude and longitude of device  |
|                  |               | format `latitude:longitude`       |
| c_xxx             | string/number | You can put your custom parameter with prefix `c_` |


Example: Report basic device with location  

```http
POST /products/A001/devices/D001/reports

{
    "data":
    {
        "state": "ERROR",
        "latitude": 12.321,
        "longitude": -32.12
    }
}
```

Example: Report custom device
```http
POST /products/A001/devices/D001/reports

{
    "data":
    {
        "state": "ERROR",
        "c_id": 5512,
        "c_temperature": 31.5,
        "c_t-unit": "°C",
        "c_pressure": 1.12,
        "c_p-unit": "atm"
    }
}
```

