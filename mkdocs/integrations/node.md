# MoBagel Node SDK   
Use MoBagel Node SDK to quickly install MoBagel to your device(s). MoBagel Node SDK is an open-source node library that makes it easy to integrate your node application with MoBagel. 


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
You can set a custom name for each property. For example, if your ID is `c_012421`, you can set the name as `temperature`. The modules in the dashboard will display your property name instead of your property ID.

* **Type**:   
There are two types of properties: `number` and `string`.

**_Please note that you must configure your properties in your configuration before you send your first customized report._**

---
# Installation
## Supported Platform
Operating System: Windows, OS X, Linux and [more](https://nodejs.org/en/download/)

## Requirement
[Node.js](https://nodejs.org/)

## Installing SDK

```
npm install mobagel-node-sdk
```

or [download directly from GitHub](https://github.com/MOBAGEL/mobagel-node-sdk)


---
# Example Walkthrough

## Registering your first device

Once you generated a product_key from the dashboard, you can use the product_key and registerDevice function to register a device in your application.

```
var mobagel = require('mobagel-node-sdk');
var product_key = "1111111111222222222233333333334444444444555555555566666666667777";
var c = mobagel.client(product_key);

c.registerDevice({
    s_string: 'Node SDK',
    d_number: 123
}, function(err, res, body) {
    if (err) throw err;
    if (Math.floor(res.statusCode / 100) === 2) {
        console.log('Response data: ');
    }
    console.log(body);
});

```

## Connecting custom properties or events

In your device application, you will need to prepare your report before sending it to MoBagel.  

* Determining different `states` of your devices to send along with your report

```
//example states

"state": "normal"
"state": "error"
```

* Adding custom properties or events with a key beginning with `c_`
    
```
//example custom properties or events

"d_temperature": 30
"s_event": "turned_on"
```

* Deciding when to send reports (time, frequency, events)

## Sending first report
```
var mobagel = require('mobagel-node-sdk');
var product_key = "";
var device_key = "1111111111222222222233333333334444444444555555555566666666667777";
var c = mobagel.client(product_key, device_key);

c.sendReport({
    state: 'normal',
    s_category: 'nodeSDK',
    d_numeric: 123
}, function(err, res, body) {
    if (err) throw err;
    if (Math.floor(res.statusCode / 100) === 2) {
        console.log('Response data: ');
    }
    console.log(body);
});
```