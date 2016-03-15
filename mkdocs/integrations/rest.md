# REST API

# Overview
This section covers the basics of the MoBagel API and how you can utilize MoBagel's platform to improve your IoT devices.

# API List

+ Register API: Register a new device
+ Report API: Send a report

# Register API
This API is used to register a new device for your product. You can simply use this API to generate mass devices to do mass deployment. However, your devices is limited. Please use this API carefully to avoid reaching the limitation of your account.

### Request
+ Method: `POST`
+ URL: `https://api.mobagel.com/v2/register`
+ Header:
    * Product-Key: The product key you get on the dashboard
+ Body:

| Parameter        | Type          | Description                       |
| :--:             | :-----:       | :----                             |
| None            |         |   |

+ Example:
```
{}
```

### Response
Success response
+ HTTP status code: 200
+ Body:
```
{
    "data": "aDeviceKey",
    "timestamp": 1412343212
}
```

Fail response
+ HTTP status code: not 200
+ Body:
```
{
    "message": "errorMessage",
    "timestamp": 1412343212
}
```

### Report API
This API is used to report the state of your devices. The report content can be customised to what you want. If you would like to report the temperature of your device, just use add `c_` as the prefix.
![report](../../img/docs/report.png)

### Request
+ Method: `POST`
+ URL: `https://api.mobagel.com/v2/reports`
+ Header:
    * Device-Key: The device key you just register on the above
+ Body:
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