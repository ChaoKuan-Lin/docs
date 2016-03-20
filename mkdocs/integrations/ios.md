# MoBagel-ios-SDK   
Use MoBagel-ios-SDK to quickly install MoBagel to your device(s). MoBagel-ios-SDK is an open-source ios library that makes it easy to integrate your ios application with MoBagel. 


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
Platform: ios

## Requirement
To install `MoBagel-ios-SDK` on your device, you need the following tool in your ios environment.  

'AFNetworking', '~> 2.3'

## Installing SDK
MoBagelSDK is available through CocoaPods. To install it, simply add the following line to your Podfile:

```
pod "MoBagel", '~> 1.0.0'
```


---
# Example Walkthrough

## Full Example

Please refer to example codes in [Github](https://github.com/MOBAGEL/mobagel-ios-sdk/tree/master/Example)


## Registering your first device

Using your `product_key` from the dashboard, you can replace the default `product_key` in /examples/main.cpp to your own `product_key`. 

```
// create mobagel object
string product_key = "[your_product_key]";
MoBagel *mobagel = new MoBagel(product_key);
```

You can then use the `registerDevice` function to register a `device` in your application.

```
// register a device
string device_key = mobagel->registerDevice();
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
report_content = [
       "state": "normal",
       "c_humidity": 30,
       "c_function": "humidify" , 
       "c_temperature": 80 
   ]


let reportData: [String : String] = `sample_report`

```
