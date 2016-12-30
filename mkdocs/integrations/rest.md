# REST API

This section covers the basics of the MoBagel API and how you can utilize MoBagel's platform to improve your IoT devices.

----
# API List

####[`Register API`](#Register)
* Register a new device for your product.

####[`Report API`](#Report)
* Send a report.


<a name="Register"></a>

----
# Register API
This API is used to register a new `Device` for your `Product`.  
You can simply use this API to generate mass devices to do mass deployment. However, your devices are limited. Please use this API carefully to avoid reaching the limitation of your account.

### Request
+ Method: `POST`
+ URL: `https://api.mobagel.com/v2/register`
+ Headers:
    * `Product-Key`: The Product Key you get on the dashboard. (Under `Basic Information` in **_Configeration -> Product Settings_**)
    * `Content-Type`: application/json
+ Body (Choose one below to send):
    * Fill in an `Empty State`.  
      `{}`
    * Fill in `Device Attribute` you have set on the dashboard. (Under `Device Settings` in **_Configeration -> Product Settings_**)  
      `
      {
        "c_temp": "1",
        "c_motion": "2",
      }
      `  
      (This serves as an example, please use the attributes you have manaually set.)


### Response
+ Success response:
    * `HTTP status code`: 200
    * `Body`:
```
{
  "_id": "An id will be generated automatically.",
  "key": "A key will be genereated here for each new device.",
  "productId": "A productId will be generated automatically.",
  "createdAt": "A timestamp of the time created.",
  "updatedAt": "A timestamp of the time updated.",
  "activatedAt": "0001-01-01T00:00:00Z",
  "properties": {
    "c_temp": "1",
    "c_motion": "2",
  }
}
```
<!---

+ Fail response:
    * `HTTP status code`: not 200
    * `Body`:
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
--->

<a name="Report"></a> 

----
### Report API
This API is used to report the state of your devices. The report content can be customised to what you want. If you would like to report the temperature of your device, just use add `c_` as the prefix.

### Request
+ Method: `POST`
+ URL: `https://api.mobagel.com/v2/report`
+ Headers:
    * `Device-Key`: The Device Key of a created device. (Under `Device List` in **_Configeration -> Device Management_**)
+ Body:

| Parameter        | Type          | Description                       |
| :--:             | :-----:       | :----                             |
| state            | string        | State of device                   |
| c_xxx            | string/number | Custom parameters must start with prefix `c_` |

An example would look like this. 
      `
      {
        "state": "Normal",
        "c_temp": "99",
        "c_motion": "100"
      }
      `


### Response
+ Success response:
    * Returns an id string.

<!---
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
--->
