# MoBagel iOS SDK   
Use MoBagel iOS SDK to quickly install MoBagel to your device(s).  MoBagel iOS SDK is an open-source iOS library that makes it easy to integrate your iOS application with MoBagel. 
​
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
​
---
# Installation

* iOS
​
## Requirement

['AFNetworking', '~> 2.3'](https://github.com/AFNetworking/AFNetworking)

## Installing SDK
`MoBagel iOS SDK` is available through [CocoaPods](http://cocoapods.org/). To install the SDK, simply add the following line to your Podfile:
​
```
pod "MoBagel", '~> 1.0.0'
```
---
# Example Walkthrough (Swift)


## Registering your first device
​
Using your `product_key` from the dashboard, you can replace the default `product_key` to your own `product_key` as following. 
​

```
#import <MoBagel/MoBagel.h>

MoBagelHandler* handler = [[MoBagelHandler alloc] init];
MoBagelClient* client = [MoBagelClient clientWithProductKey:productKey];

self.handler.apiHandler =  ^(NSInteger code, id responseObject) {
    // responseObject contain deviceId && deviceKey
    NSLog(@"ResponseObject: %@",responseObject);
};

self.handler.exceptionHandler =  ^(NSInteger code, id responseObject) {
    NSLog(@"Exception: %@",responseObject);
};
[client register:@{} handler:handler];
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

* Adding custom properties or events with a key beginning with `s_` or `d_`

    
```
//example custom properties or events
​
"d_temperature": 30
"s_event": "turned_on"
```

* Deciding when to send reports (time, frequency, events)

## Sending first report

​You need `device-key` to send a report.  
If you see `report response` , congratulations! You have successfully send a report.  

```
#import <MoBagel/MoBagel.h>

MoBagelHandler* handler = [[MoBagelHandler alloc] init];
MoBagelClient* client = [MoBagelClient clientWithDeviceKey:deviceKey];

self.handler.apiHandler =  ^(NSInteger code, id responseObject) {
    // responseObject contain deviceId && deviceKey
    NSLog(@"ResponseObject: %@",responseObject);
};

self.handler.exceptionHandler =  ^(NSInteger code, id responseObject) {
    NSLog(@"Exception: %@",responseObject);
};

NSDictionary* data = @{
    @"state": @"normal",
    @"d_temperature": @(30),
    @"s_event": @"turned_on",
};
[client report:data handler:handler];
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