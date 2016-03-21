# MoBagel Node SDK   
Use MoBagel Node SDK to quickly install MoBagel to your device(s). MoBagel Node SDK is an open-source node library that makes it easy to integrate your node application with MoBagel. 


---
# Preparation
## Creating an account
If you do not have an account, please create an account [here](https://app.mobagel.com/signup). After you create an account, you will be directed to the dashboard.

## Creating a new product  
To use MoBagel, you first have to create a `product`, which is a parent class of a `device`. You can create new products in the dashboard. 

For example:     

 * [Product Name] iBulb
 * [Product Brief] Smart light bulb
 * [Product Description] Wi-Fi connected light bulb with motion sensors and temperature sensors.

## Locating your product key
After you create a `product`, the system will generate a `product_key`, which will be used to create `device` later on.

To find your `product_key`, go to Overview -> Product List -> Click on your product.


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
