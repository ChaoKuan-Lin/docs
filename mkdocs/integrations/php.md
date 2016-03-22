# MoBagel PHP SDK   
Use MoBagel PHP SDK to quickly install MoBagel to your device(s).MoBagel PHP SDK is an open-source php library that makes it easy to integrate your php application with MoBagel. 


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
## Requirement
You need to download [composer.](https://getcomposer.org/download/)

## Installing SDK
```
composer install mobagel/mobagel-php-sdk
```
or [download directly from GitHub](https://github.com/MOBAGEL/mobagel-php-sdk)

---
# Example Walkthrough
## Full Example

```
<?php

// require dependencies
require 'vendor/autoload.php';

// setup your product key
$productKey = "YOUR_PRODUCT_KEY";

// register a new device
$deviceKey = \MoBagel\MoBagel::registerDevice($productKey);

// use device key to report
$contents = [
    "state" => "normal",
    "c_foo" => "bar",
];
$ret = \MoBagel\MoBagel::sendReport($deviceKey, $contents);

print_r($ret);

```

## Registering your first device

Using your `product_key` from the dashboard, you can replace the default `product_key` in /examples/main.cpp to your own `product_key`. 

```
$deviceKey = \MoBagel\MoBagel::registerDevice($productKey);
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

"c_temperature": 30
"c_event": "turned_on"
```

* Deciding when to send reports (time, frequency, events)

## Sending first report

```
$contents = [
    "state" => "normal",
    "c_foo" => "bar",
];
$ret = \MoBagel\MoBagel::sendReport($deviceKey, $contents);

print_r($ret);
```

## Compiling the application

If you receive the following response, then your request has been successfully sent to MoBagel and your registered device and report will appear in your MoBagel dashboard.

```
Array
(
    [data] => 56e7b690f8e9d3ee478b4567
    [timestamp] => 1458026061
)
```
