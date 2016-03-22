# MoBagel iOS SDK   
Use MoBagel iOS SDK to quickly install MoBagel to your device(s).  MoBagel iOS SDK is an open-source iOS library that makes it easy to integrate your iOS application with MoBagel. 
​
---
# Preparation
## Creating an account
If you do not have an account, please create an account [here](https://app.mobagel.com/signup). After you create an account, you will be directed to the dashboard.
​
## Creating a new product  
To use MoBagel, you first have to create a `product`, which is a parent class of a `device`. You can create new products in the dashboard. 

For example:     

 * [Product Name] iBulb
 * [Product Brief] Smart light bulb
 * [Product Description] Wi-Fi connected light bulb with motion sensors and temperature sensors.

## Locating your product key
After you create a `product`, the system will generate a `product_key`, which will be used to create `device` later on.
​
To find your `product_key`, go to Overview -> Product List -> Click on your product.
​
---
# Installation
## Supported Platform

* iOS
​

## Requirement

['AFNetworking', '~> 2.3'](https://github.com/AFNetworking/AFNetworking)
​

## Installing SDK
`MoBagel iOS SDK` is available through [CocoaPods](http://cocoapods.org/). To install the SDK, simply add the following line to your Podfile:
​
```
pod "MoBagel", '~> 1.0.0'
```
---
# Example Walkthrough (Swift)
## Full Example
​
Please refer to example codes in [Github](https://github.com/MOBAGEL/mobagel-iOS-sdk/tree/master/Example)
​
## Import Framework
Please import MoBagel iOS SDK as following.
​
```
 #import Mobagel
```
## Registering your first device
​
Using your `product_key` from the dashboard, you can replace the default `product_key` to your own `product_key` as following. 
​
```
// create MobagelClient object
let client = MoBagelClient.init(key: "<#Put your product_key here#>")
​
```
​
You can then use the `registerDevice` function to register a `device` in your application.  
If you get your `device-key` , congratulations! You have successfully register a device.  
​
```
let handler = MoBagelHandler();
handler.registerHandler = {(code, data) -> Void in
    print("Http code: \(code) , device-key: \(data)");
    let key = data
    // Store your key here
}
handler.exceptionHandler = {(code, error) -> Void in
    print("Http code: \(code) , Error msg: \(error)");
}
client.registerDevice(handler)
​
​
```
## Connecting custom properties or events
​
In your device application, you will need to prepare your report before sending it to MoBagel.  

* Determining different `states` of your devices to send along with your report
​

```
//example states
​
"state": "normal"
"state": "error"
```

* Adding custom properties or events with a key beginning with `c_`

    
```
//example custom properties or events
​
"c_temperature": 30
"c_event": "turned_on"
```

* Deciding when to send reports (time, frequency, events)

## Sending first report

​You need `device-key` to send a report.  
If you see `report response` , congratulations! You have successfully send a report.  

```
let device = MoBagelDevice.init(key: <#device-key#>)
let handler = MoBagelHandler();
handler.apiHandler = {(code, data) -> Void in
    print("Http code: \(code) , report response: \(data)");
}
handler.exceptionHandler = {(code, error) -> Void in
    print("Http code: \(code) , Error msg: \(error)");
}
let reportData: [String : String] = [
    "state" : "normal",
    "c_temperature": 30,
    "c_event": "turned_on",
]
device.report(reportData, handler: handler)
```

<!-- 
# Swift Sample code
## Import framework

```
import MoBagel
```
## Register device

Using your `product_key` from the dashboard, you can replace the default `product_key` in /examples/main.cpp to your own `product_key`.  
If you get your `device-key` , congratulations! You have successfully register a device.

```
let client = MoBagelClient.init(key: "1111111111222222222233333333334444444444555555555566666666667777")
let handler = MoBagelHandler();
handler.registerHandler = {(code, data) -> Void in
    print("Http code: \(code) , device-key: \(data)");
    let key = data
    // Store your key here
}
handler.exceptionHandler = {(code, error) -> Void in
    print("Http code: \(code) , Error msg: \(error)");
}
client.registerDevice(handler)
```
## Send report
You need `device-key` to send a report.  
If you see `report response` , congratulations! You have successfully send a report.  

```
let device = MoBagelDevice.init(key: <#device-key#>)
let handler = MoBagelHandler();
handler.apiHandler = {(code, data) -> Void in
    print("Http code: \(code) , report response: \(data)");
}
handler.exceptionHandler = {(code, error) -> Void in
    print("Http code: \(code) , Error msg: \(error)");
}
let reportData: [String : String] = [
    "state" : "normal",
    "c_platform" : "iOS"
]
device.report(reportData, handler: handler)
```
​ -->