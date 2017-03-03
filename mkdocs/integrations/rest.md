# REST API

This section covers the basics of the MoBagel API and how you can utilize MoBagel's platform to improve your IoT devices.

---

# Preparation

# Creating an account
If you do not have an account, please create an account [here](https://app.mobagel.com/login). After you create an account, you will be directed to the dashboard.
<img src="../../../img/MoBagel_Getting_Started/Sign_up.png" width="800">  

---
# Creating a new product
To use MoBagel, you first have to create a `product`, which is essentially a group of same `device`. You will be prompted to create a new product when you first enter the dashboard.

<img src="../../../img/MoBagel_Getting_Started/Enter_Product_name.png" width="800">  

After you create a `product`, you can go to **_Configuration -> Product Settings_** Info to retrieve your `product_key`, which will be used to create `device` later on.

<img src="../../../img/MoBagel_Getting_Started/Product_key.png" width="800">  

---
# Adding custom properties

<img src="../../../img/MoBagel_Getting_Started/Config_settings.png" width="200">   
In **_Product Settings_** under **_Configuration_**, you can add custom properties to your product.   
Custom properties should have the following requirements:   

<img src="../../../img/MoBagel_Getting_Started/Device_Settings.png" width="800">   

* **ID**:   
Property ID will always begin with `d_` (for numbers) or `s_` (for strings) to indicate that it is a custom property, this will be automatically asigned when you select a `Type`. Property IDs are unique and cannot repeat with itself.

* **Name**:   
You can set a custom name for each property. For example, if your ID is `d_012421`, you can set the name as `temperature`. The modules in the dashboard will display your property name instead of your property ID.

* **Type**:   
There are two types of properties: `number` and `string`.

**_Please note that you must configure your properties in your configuration before you send your first customized report._**

----

# API List

####[`Register API`](#Register)
* Register a new device for your product.

####[`Report API`](#Report)
* Send a report 


<a name="Register"></a>

----

# Register API
This API is used to register a new `Device` for your `Product`.  
You can simply use this API to generate mass devices to do mass deployment. However, your devices are limited. Please use this API carefully to avoid reaching the limitation of your account.

----

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
        "d_numeric": 11,
        "s_category": "11"
      }
      `  

----

### Response

+ Successful response example:
    * `HTTP status code`: 201
    * `Body`:
```
{
  "id": "5881c64f0136eef58c4ed83d",
  "key": "e189a3a2dc8212da87c95043c26204e8efd98f2c07b66a6f126d3ca58b2cafec"
}
```

+ Failed response example:
    * `HTTP status code`: any other code than 201
    * `Body`:
```
{
  "msg": "Key: c7aa3cff154001ec458fc9eb51f1a377b27a7348ae302bdc84098e8b9946c58 does not validate as length(64|64);"
}
```

<a name="Report"></a> 

----

# Report API
This API is used to report the state of your devices. The content can be customised, with custom properties beginning with `d_` (for numbers) or `s_` (for strings) to indicate that it is a string.

----

### Request
+ Method: `POST`
+ URL: `https://api.mobagel.com/v2/report`
+ Headers:
    * `Device-Key`: The Device Key of a created device. (Under `Device List` in **_Configeration -> Device Management_**)
+ Body:

```
{
  "d_numeric": 11,
  "s_category": "11"
}
```

----

### Response
+ Successful response example:
    * Returns an `id string`.

```
{
"id": "5881d17e0136eef58c4ee212"
}
```

+ Failed response example:
    * `HTTP status code`: any other code than 201
    * `Body`:
```
{
  "msg": "No device key in headers."
}
```

