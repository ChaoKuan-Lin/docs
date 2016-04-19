# MoBagel Node SDK   
Use MoBagel Node SDK to quickly install MoBagel to your device(s). MoBagel Node SDK is an open-source node library that makes it easy to integrate your node application with MoBagel. 


---
# Preparation

## Creating an account
If you do not have an account, please create an account [here](https://app.mobagel.com/signup). After you create an account, you will be directed to the dashboard.

## Creating a new product  
To use MoBagel, you first have to create a `product`, which is essentially a group of same `device`. You will be prompted to create a new product when you first enter the dashboard.

After you create a `product`, you can go to Configuration -> Device Info to retrieve your `product_key`, which will be used to create `device` later on.

## Adding custom properties

In the Configuration, you can add custom properties to your product. Custom properties should have the following requirements:

* **ID**: Property ID (with the exception of `state`) should always begin with `c_` to indicate that it is a custom property. In addition, property IDs are unique and cannot repeat with itself.

* **Name**: The property name is your nickname for your property. For example, if your ID is 'c_012421', you can set the name as 'temperature'. The modules in the dashboard will display your property name instead of your property ID.

* **Type**: There are two types of properties: category and numeric. Category uses a set of string options and numeric uses numeric options (optional).

* **Options**:
    - **Category**: please add all the possible string values of your property by typing in the options column. The server will use this to prevent your devices from sending erroraneous reports.
    
    - **Numeric** (optional): please set a min and max value for your numeric property to help protect your data from errors. For example, if your numeric property is humidity level, then you can set min and max to 0 and 100, respectively. This will allow our system to reject any reports with humidity levels that are not in this range because those values are theoretically impossible (i.e. negative humidity level).

Please note that you must configure your properties in your configuration before you send your first customized report.


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
## Full Example

```javascript
var mobagel = require('mobagel-node-sdk');

var device_key = YOUR_DEVICE_KEY
var device = mobagel.client(device_key);

device.sendReport({
    state: 'normal',
    c_temperature: 123,
    c_pressure: 123.12,
    c_label: 'test'
}, function(err, res, body) {
    if (err) throw err;
    console.log('sendReport response: ' + JSON.stringify(body));
});
```
## Registering your first device

Using your `product_key` from the dashboard, you can replace the default `product_key` in /examples/main.cpp to your own `product_key`. 

```
var mobagel = require('mobagel-node-sdk');

var product_key = YOUR_PRODUCT_KEY;
var product = mobagel.admin(product_key);

product.registerDevice(function(err, res, body) {
    if (err) throw err;
    if (res.statusCode === 200) {
        device_key = body.data;
        console.log('The key of the new device: ' + device_key);
    } else {
        console.log(body.message);
    }
});

```

## Connecting custom properties or events

In your device application, you will need to prepare your report before sending it to MoBagel.

* Determining different `states` of your devices to send along with your report

```
// example states

"state": "normal"
// or
"state": "error"

```

* Adding custom properties or events with a key beginning with `c_`
    
```
//example custom properties or events

"c_temperature": 30
"c_event": "turned_on"
```

* Deciding when to send reports (time, frequency, events)

## Sending first report

```javascript
var mobagel = require('mobagel-node-sdk');

var device_key = YOUR_DEVICE_KEY
var device = mobagel.client(device_key);

device.sendReport({
    state: 'normal',
    c_temperature: 123,
    c_pressure: 123.12,
    c_label: 'test'
}, function(err, res, body) {
    if (err) throw err;
    console.log('sendReport response: ' + JSON.stringify(body));
});
```
