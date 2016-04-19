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
# Example Walkthrough (Objective-C)
## Full Example
​
Please refer to example codes in [Github](https://github.com/MOBAGEL/mobagel-iOS-sdk/tree/master/Example)
​
## Import Framework
Please import MoBagel iOS SDK as following.
​
```
 #import <MoBagel/MoBagel.h>
```
## Registering your first device
​
Using your `product_key` from the dashboard, you can replace the default `product_key` to your own `product_key` as following. 
​
```
// create MobagelClient object
MoBagelClient* client = [[MoBagelClient alloc] initWithKey:@"<#Put your product_key here#>"];

```
​
You can then use the `registerDevice` function to register a `device` in your application.  
​If you get your `device-key` , congratulations! You have successfully register a device.  

```
// register a device
MoBagelHandler* handler = [[MoBagelHandler alloc] init];
​
[handler setRegisterHandler:^(NSInteger code, NSString* data){
    NSLog(@"Http code: %d , device-key: %@",code, data);
​
    NSString* key = data;
    // Store this key
}];
[handler setExceptionHandler:^(NSInteger code, NSError* error){
    NSLog(@"Http code: %d , Error msg: %@",code, error);
}];
​
[client registerDevice:handler];
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
@"state": @"normal"
@"state": @"error"
```

* Adding custom properties or events with a key beginning with `c_`

```
//example custom properties or events
​
@"c_temperature": 30
@"c_event": @"turned_on"
```

* Deciding when to send reports (time, frequency, events)
​

## Sending first report

​You need `device-key` to send a report.  
If you see `Update device` , congratulations! You have successfully send a report.  

```
NSString* device_key = @"<#Get your device key#>";
​
MoBagelDevice* device = [[MoBagelDevice alloc] initWithKey:device_key];
​
MoBagelHandler* handler = [[MoBagelHandler alloc] init];
[handler setApiHandler:^(NSInteger code, NSString* data){
    NSLog(@"Http code: %d , Update device: %@",code, data);
}];
[handler setExceptionHandler:^(NSInteger code, NSError* error){
    NSLog(@"Http code: %d , Error msg: %@",code, error);
}];
​
NSDictionary* reportData = @{
                              @"state": @"normal",
                              @"c_temperature": 30,
                              @"c_event": @"turned_on",
                             };
    // Put your properties or events for report here
​
[device device:reportData
       handler:handler];
​
​
```
<!-- ---
# Objective-C Sample code
## Import framework

```
 #import <MoBagel/MoBagel.h>
```
## Register device

Using your `product_key` from the dashboard, you can replace the default `product_key` in /examples/main.cpp to your own `product_key`.  
If you get your `device-key` , congratulations! You have successfully register a device.  

```
MoBagelClient* client = [[MoBagelClient alloc] initWithKey:@"1111111111222222222233333333334444444444555555555566666666667777"];
MoBagelHandler* handler = [[MoBagelHandler alloc] init];

[handler setRegisterHandler:^(NSInteger code, NSString* data){
    NSLog(@"Http code: %d , device-key: %@",code, data);

    NSString* key = data;
    // Store this key
}];
[handler setExceptionHandler:^(NSInteger code, NSError* error){
    NSLog(@"Http code: %d , Error msg: %@",code, error);
}];

[client registerDevice:handler];
```

## Send report

You need `device-key` to send a report.  
If you see `Update device` , congratulations! You have successfully send a report.  

```
NSString* device_key = @"<#Get your device key#>";

MoBagelDevice* device = [[MoBagelDevice alloc] initWithKey:device_key];

MoBagelHandler* handler = [[MoBagelHandler alloc] init];
[handler setApiHandler:^(NSInteger code, NSString* data){
    NSLog(@"Http code: %d , Update device: %@",code, data);
}];
[handler setExceptionHandler:^(NSInteger code, NSError* error){
    NSLog(@"Http code: %d , Error msg: %@",code, error);
}];

NSDictionary* reportData = @{
                              @"state" : @"available",
                              @"c_develop_zone" : @"iOS",
                             };

[device device:reportData
       handler:handler];
``` -->