# MoBagel iOS SDK   
Use MoBagel iOS SDK to quickly install MoBagel to your device(s).  MoBagel iOS SDK is an open-source iOS library that makes it easy to integrate your iOS application with MoBagel. 
​
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