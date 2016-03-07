# MoBagelSDK

[![Version](https://img.shields.io/cocoapods/v/MoBagelSDK.svg?style=flat)](http://cocoapods.org/pods/MoBagelSDK)
[![License](https://img.shields.io/cocoapods/l/MoBagelSDK.svg?style=flat)](http://cocoapods.org/pods/MoBagelSDK)
[![Platform](https://img.shields.io/cocoapods/p/MoBagelSDK.svg?style=flat)](http://cocoapods.org/pods/MoBagelSDK)

## Introduce

MoBagel is a real-time cloud analytics platform that helps IoT companies monitor and analyze hardware usage, speed up research and development, forecast sales and marketing strategies, and proactively engage with customers to prevent product returns. As a result, companies can also save up to millions in cost reductions.

 
[More detail](https://mobagel.com/features)

## Usage

To run the example project, clone the repo, and run `pod install` from the Example directory first.

## Requirements
'AFNetworking', '~> 2.3'  
'AESCrypt', '~> 0.0.1'

## Installation

MoBagelSDK is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "MoBagelSDK", '~> 0.3.0'
```

## How it work!

1. Register in our dashboard ! (You can visit [https://app.mobagel.com](https://app.mobagel.com))
2. Initialize BagelDevice object
3. Fill with your device information 
    * product_id
    * product_key
    * device_id
    * device_key
4. Start report!!  
There is only one function call 'report' in BagelDevice class, You need to pass your report data (NSDictionary) and handle data response

| Parameter | 	Type | 	Description |  
| --- | 	--- | 	--- | 
| state(mandatory) | string | State of device |  
| latlng(optional) | string | Latitude and longitude of device format latitude:longitude |  
| c_xxx | string/number | You can put your custom parameter with prefix c_ |  

## Objective-C Sample code 
```
#import <MoBagelSDK/BagelDevice.h>
```
```
BagelDevice* device = [BagelDevice new];
device.product_id = @"<#product_id#>";
device.product_key = @"<#product_key#>";
device.device_id = @"<#device_id#>";
device.device_key = @"<#device_key#>";
  
id data = {<#Fill report data#>}
[device report:data
       success:^(NSInteger code, NSString *data) {
          <#Handle success response#>
       }
       failure:^(NSInteger code, NSError *error) {
          <#Handle fail response#>
       }];
```

## Swift Sample code 
```
import MoBagelSDK
```
```
let device = BagelDevice()
device.product_id = "<#product_id#>"
device.product_key = "<#product_key#>"
device.device_id = "<#device_id#>"
device.device_key = "<#device_key#>"

let data = NSDictionary()
device.report(data as [NSObject : AnyObject],
   success: { (code, data) -> Void in
       <#Handle success response#>
   }) { (code, error) -> Void in
       <#Handle fail response#>
}
```

## More
You can visit our home page and get more information.
[https://mobagel.com](https://mobagel.com)

## Author

Ken Lin, can@mobagel.com

## License

MoBagelSDK is available under the MIT license. See the LICENSE file for more info.
