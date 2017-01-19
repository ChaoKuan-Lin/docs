# MoBagel Python SDK   
Use MoBagel Python SDK to quickly install MoBagel to your device(s). MoBagel Python SDK is an open-source python library that makes it easy to integrate your python application with MoBagel. 

---

# Preparation

# Creating an account
If you do not have an account, please create an account [here](https://app.mobagel.com/signup). After you create an account, you will be directed to the dashboard.
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

​---  

## Installation
Before you run mobagel-python-sdk, you need to install [pip](https://pip.pypa.io/en/stable/) first.

pip (Mac OS X)
```shell
    $ sudo easy_install pip
```

pip (Ubuntu 14.04)
```shell
    $ sudo apt-get install python-pip python-dev build-essential 
    $ sudo pip install --upgrade pip 
```

mobagel-python-sdk
```shell
    $ sudo pip install mobagel-python-sdk
```

---
# Example Walkthrough

## Registering your first device

Once you generated a product_key from the dashboard, you can use the product_key and registerDevice function to register a device in your application.

```
# ENV: python3.5.1 / python2.7.6
import json
import pybagel

# Initialize a Client Instance by product_key
c = pybagel.MoBagelClient()
c.product_key="YOUR_PRODUCT_KEY"

# Custom properties, should be created in the MoBagel dashboard
content = {
    "s_string": "PythonSDK",
    "d_number": 100
}

# register a new device
status_code, body = c.registerDevice(content)
response = json.loads(body.decode('utf-8'))

# return a new device_key
print("Status code:", status_code)
print("Response data:", response)
print("Device Key:", response["key"])

```

## Connecting custom properties or events

In your device application, you will need to prepare your report before sending it to MoBagel.  

* Adding custom properties or events with a key beginning with `d_` or `s_`
    
```
//example custom properties or events

"d_temperature": 30
"s_event": "turned_on"
```

## Sending first report
```
# ENV: python3.5.1 / python2.7.6
import json
import pybagel

# Initialize a Client Instance by product_key
# You can register a device and get a device_key according "example_registerDevice.py"
c = pybagel.MoBagelClient()
c.device_key="YOUR_DEVICE_KEY"

# Custom properties, should be created in the MoBagel dashboard
content = {
    "s_category": "PythonSDK",
    "d_numeric": 999
}

# send report with device key
status_code, body = c.sendReport(content)
response = json.loads(body.decode('utf-8'))

# return status_code, product_id
print("Status code:", status_code)
print("Response data:", response)
```