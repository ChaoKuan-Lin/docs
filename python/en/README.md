# mobagel-python-sdk

## Introduce

MoBagel is a real-time cloud analytics platform that helps IoT companies monitor and analyze hardware usage, speed up research and development, forecast sales and marketing strategies, and proactively engage with customers to prevent product returns. As a result, companies can also save up to millions in cost reductions.

## Usage

To run the example project, clone the repo, and run pip install from the Example directory first.

## How it work!

1. Register in our dashboard ! (You can visit [https://app.mobagel.com](https://app.mobagel.com))
2. Initialize BagelDevice object
3. Fill with your device information 
    * product_id
    * product_key
    * device_id
    * device_key
4. Start report!!  
There is only one function call 'report' in BagelDevice class, You need to pass your report data (HashMap<String, Object>) and handle data response

| Parameter | 	Type | 	Description |  
| --- | 	--- | 	--- | 
| state(mandatory) | string | State of device |  
| latlng(optional) | string | Latitude and longitude of device format latitude:longitude |  
| c_xxx | string/number | You can put your custom parameter with prefix c_ |  

## Sample code 

``` Python
import pybagel
```
```
my_device_config = {
    "product_id": <#product_id#>,
    "product_key": <#product_keyy#>,
    "device_id": <#device_id#>,
    "device_key": <#device_key#>
    }

myclient = pybagel.Client(device_config=my_device_config)

print myclient.getTime()

report_content = {
                    "data": {
                        "state": "normal",   ## state field is necessary
                        }
                 }

ret = myclient.sendReport(report_content)

print ret
```

## More
You can visit our home page and get more information.
[https://mobagel.com](https://mobagel.com)

## Author

MoBagel, us@mobagel.com

## License

MoBagel Software Development Kit (SDK) License Agreement


Subject to the terms of this License Agreement, you are hereby granted a worldwide, royalty-free, non-assignable, non-exclusive, and non-sublicensable license to use, copy, modify, and distribute this software in source code or binary form to use the SDK solely to develop applications to connect with MoBagel’s platform.

MoBagel owns all legal right, title and interest in and to the SDK. MoBagel reserves all rights not expressly granted to you. 

The form and nature of the SDK that MoBagel provides may change without prior notice to you. This SDK is provided “as is”, without warranty of any kind, express or limited. MoBagel may stop (permanently or temporarily) providing the SDK to users at MoBagel's sole discretion without prior notice.

You are not granted the right to use MoBagel’s trademarks, logos, domain names, or other distinctive brand features. 
