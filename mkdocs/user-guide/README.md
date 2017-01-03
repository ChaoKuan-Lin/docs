# API Spec

Last Updated: 2016/02/03 Kevin Shyu
Coptright at MoBagel

## Prerequirements

### Request
To access the MoBagel API, you first have to set up http headers. Add the following headers to your requests:

+ product_id
+ device_id
+ timestamp
+ token

**Note:** `token = SHA256( product_id:product_key:device_id:device_key:timestamp )`

If you use `POST` method, the Content-Type must be `application/json`, and the post data should follow the format below:

    {
        "data": {
            "field": "value"
        }
    }

**Note:** field will be defined by each API

### Response
For each response, the format will look like:

    {
        "code": $code,
        "timestamp": $timestamp,
		"message": $message,
        "data": $data
    }


## API List

Host: `https://api.mobagle.com`

*List by priority*

|Name					|	Method	|Route				
|:---------------------:|:---------:|:------------------
|Get Time				|	GET		|/time
|Send Report			|	POST	|/products/{product_id}/devices/{device_id}/reports/
|Get Reports			|	GET		|/products/{product_id}/devices/{device_id}/reports/
|Get Specific Report	|	GET		|/products/{product_id}/devices/{device_id}/reports/{report_id}
|Set Device				|	POST	|/products/{product_id}/devices/{device_id}
|Get Device				|	GET		|/products/{product_id}/devices/{device_id}
|Send Command			|	POST	|/products/{product_id}/devices/{device_id}/commands/
|Get Commands			|	GET		|/products/{product_id}/devices/{device_id}/commands/
|Get Specific Command	|	GET		|/products/{product_id}/devices/{device_id}/commands/{command_id}
|Set Relative			|	POST	|/products/{product_id}/devices/{device_id}/relatives
|Get Relative			|	GET		|/products/{product_id}/devices/{device_id}/relatives

**NOTE:** After finishing Relative API, masters can use all the APIs to their slaves.

### Get Time
Return current timestamp from server


+ Example:
	- Get current server timestamp
		Request: `GET /time`
		Response: 
		```http
		1454469325123
		```
		

* **URL**

  `/time`

* **Method:**
  
  `GET`
  
*  **URL Params**

   None

* **Data Params**

  None

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** 
    ```http
    1454469325123
    ```
 
* **Sample Call:**

  ```js
  $.ajax({
    url: "/time",
    type : "GET",
    success : function(r) {
      console.log(r);
    }
  });
  ```

* **Notes:**

  All the MoBagel API use milliseconds(13-digit) as the timestamp unit.

### Send Report
Send report from specific device
`POST	/products/{product_id}/devices/{device_id}/reports/`
| Parameter        | Type          | Description                       |
| :--:             | :-----:       | :----                             |
| state            | string        | State of device                   |
| latlng(optional) | string        | Latitude and longitude of device  |
|                  |               | format `latitude:longitude`       |
| custom           | string/number | You can put your custom parameter |


Example: Report basic device with location
```http
POST /products/A001/devices/D001/reports

{
    "data":
    {
        "state": "FATAL_ERROR",
        "latlng": "12.321:-32.12"
    }
}
```

Example: Report custom device
```http
POST /products/A001/devices/D001/reports

{
    "data":
    {
        "state": "FATAL_ERROR",
        "id": 5512,
        "temperature": 52.32,
        "t-unit": "celsius",
        "pressure": 1.12,
        "p-unit": "atm",
    }
}
```

### Get Reports
Get reports from specific device
`GET	/products/{product_id}/devices/{device_id}/reports/`

### Get Specific Report
Get specific report from specific device
`GET	/products/{product_id}/devices/{device_id}/reports/{report_id}`

### Set Device
Set specific device data
`POST	/products/{product_id}/devices/{device_id}`

### Get Device
Get specific device data
`GET	/products/{product_id}/devices/{device_id}`
| Parameter        | Type    | Description                                |
| :--:             | :-----: | :----                                      |
| fields (optional) | string  | Attributes of the device. Seperated by `,` |


+ Example
	- Get device's all information
		Request: `GET /products/A001/devices/D001`
		Response:
		```http
		{
			"id": "DEVICE_ID",
			"key": "DEVICE_KEY",
			"activate_time": "DEVICE_activate_time",
			"update_time": "DEVICE_UPDATE_TIME",
			"create_time": "DEVICE_CREATE_TIME",
			"product": {
				"id": "PRODUCT_ID",
				"key": "PRODUCT_KEY"
				"name": "PRODUCT_NAME",
				"brief": "PRODUCT_BRIEF",
				"description": "PRODUCT_DESCRIPTION",
				"update_time": "PRODUCT_UPDATE_TIME",
				"create_time": "PRODUCT_CREATE_TIME",
				"vendor": {
					"id": "VENDOR_ID",
					"plan": "VENDOR_PLAN"
					"name": "VENDOR_NAME",
					"brief": "VENDOR_BRIEF",
					"description": "VENDOR_DESCRIPTION",
					"update_time": "VENDOR_UPDATE_TIME",
					"create_time": "VENDOR_CREATE_TIME",
				}
			}
		}
		```
	- Get device's name, update time
		Request: `GET /products/A001/devices/D001?fields=activate_time,update_time`
		Response:
		```http
		{
			"activate_time" : 1454468591123
			"update_time" : 1454468591123
		}
		```

### Send Command
Send command from specific device
`POST	/products/{product_id}/devices/{device_id}/commands/`

### Get Commands
Get commands from specific device
`GET	/products/{product_id}/devices/{device_id}/commands/`

### Get Specific Command
Get specific commands from specific device
`GET	/products/{product_id}/devices/{device_id}/commands/{command_id}`

### Set Relative
Set master for specific device
`POST	/products/{product_id}/devices/{device_id}/relatives`

### Get Relative
Get masters and slaves for specific device
`GET	/products/{product_id}/devices/{device_id}/relatives`


## Error Handling

This section covers the basics of the MoBagel API and how you can utilize MoBagel's platform to improve your IoT devices.


---

## Vendor
The vendor or `vendor_id` is your MoBagel acccount. Each MoBagel account has a unique `vendor_id` used to distinguish your account from other MoBagel accounts.

---

## Product
The product is your IoT product. Whether you have an existing product or wish to create a new product, the product first has to be created on the platform. For example, if you are a TV manufacturer, the product is the TV. If you produce two types of TV, then you need to create two products.

To create a product, you need to give a unique global `product_id`. You cannot use an `product_id` that has already been taken by others.

After creating an product, you will receive a 64bytes `product_key` generated by MoBagel. Please store the `product_key` in a safe place as it is very important to your product.

---

## Device
Devices belongs to products. Each device belongs to a specific product, and a product may contain several devices.

To create a device, you do not have to give a `device_id`. Instead, the system will give you one.

After creating a device, you will also receive a `device_key`. Please also store the `device_key` in a safe place as it is very important to your device.

Attribute:

+ device_id
+ device_key
+ name
+ description
+ activate_time
+ update_time
+ create_time
+ masters
+ slaves
+ report_timestamp
+ report_state
+ report_ip
+ report_latlng
+ report_country
+ report_city
+ report_countrycode

#### Get device information

Method: `GET`

Path: `/products/{product_id}/devices/{device_id}`



## Relatives
Relatives are used to indicate the relationship between devices. For each device, there are two relatives, `master` and `slave`. For more information about relatives, please see [authentication](authentication.md)

#### Update device relatives

Method: `POST`

Path: `/products/{product_id}/devices/{device_id}/relatives`

| Parameter  | Type    | Description                |
| :--:       | :-----: | :----                      |
| method     | string  | Only can be `ADD` or `DEL` |
| level      | string  | Only can be `master`       |
| device_ids | array   | Device Ids yo set          |


Example: Set `D002` and `D003` as `D001` masters
```http
POST /products/A001/devices/D001/relatives

{
    "data":
    {
        "method": "ADD",
        "level": "master",
        "device_ids": ["D002", "D003"]
    }
}
```

## Command
Command can be sent to devices from users. 

![command](../../img/docs/command.png)

#### Get device commands

Method: `GET`

Path: `/products/{product_id}/devices/{device_id}/commands`

| Parameter | Type    | Description                            |
| :--:      | :-----: | :----                                  |
| limit     | int     | limit of commands, default `unlimited` |
| order     | string  | `asc` or `desc`, default `asc`         |
| filter    | string  | format `key,op,value`                  |


Example: get device last command

```http
GET /products/A001/devices/D001/commands?limit=1&order=desc
```

Example: get device commands with content "ON"

```http
GET /products/A001/devices/D001/commands?limit=1&order=desc&filter=content,==,ON
```

#### Send a command to a device

Method: `POST`

Path: `/products/{product_id}/devices/{device_id}/commands`

| Parameter | Type    | Description        |
| :--:      | :-----: | :----              |
| content   | string  | Content of command |


Example:
```http
POST /products/A001/devices/D001/commands

{
    "data":
    {
        "content": "ON"
    }
}
```


## Report
When an event such as device overheating occurs, a report is sent to the cloud.

![report](../../img/docs/report.png)

#### Get device reports

Method: `GET`

Path: `/products/{product_id}/devices/{device_id}/reports`

| Parameter | Type    | Description                            |
| :--:      | :-----: | :----                                  |
| limit     | int     | limit of reports, default `unlimited` |
| order     | string  | `asc` or `desc`, default `asc`         |
| filter    | string  | format `key,op,value`                  |


Example: get device last report

```http
GET /products/A001/devices/D001/reports?limit=1&order=desc
```

Example: get device reports with state "FATAL_ERROR"

```http
GET /products/A001/devices/D001/reports?limit=1&order=desc&filter=state,==,FATAL_ERROR
```


