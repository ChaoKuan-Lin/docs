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


### Response
Success response
+ HTTP status code: 200
+ Body:
```
{
  "data": {
    "type": "device",
    "id": "requestId",
    "attributes": {
      "key": "{YOUR_DEVICE_KEY}",
      "updatedAt": 1461062720,
      "activatedAt": 0,
      "token": [
      ],
      "createdAt": 1461062720
    }
  }
}
```

Fail response
+ HTTP status code: not 200
+ Body:
```
{
  "errors": [
    {
      "title": "{ERROR_TITLE}",
      "detail": "{ERROR_DETAIL}"
    }
  ]
}
```

### Report API
This API is used to report the state of your devices. The report content can be customised to what you want. If you would like to report the temperature of your device, just use add `c_` as the prefix.

### Request
+ Method: `POST`
+ URL: `https://api.mobagel.com/v2/report`
+ Header:
    * Device-Key: The device key you just register on the above
+ Body:

| Parameter        | Type          | Description                       |
| :--:             | :-----:       | :----                             |
| state            | string        | State of device                   |
| c_xxx             | string/number | You can put your custom parameter with prefix `c_` |


Example: Report basic device  

```http
{
    "state": "ERROR"
}
```

Example: Report custom device
```http
{
    "state": "ERROR",
    "c_id": 5512,
    "c_temperature": 31.5,
    "c_t-unit": "°C",
    "c_pressure": 1.12,
    "c_p-unit": "atm"
}
```

