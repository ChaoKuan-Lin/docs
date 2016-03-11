# MoBagel-C-SDK   
Get started quickly using MoBagel service with the MoBagel-C-SDK. The SDK is a modern, open-source C library that makes it easy integrate your C application with MoBagel service. 

## Set up your account
To use MoBagel API, you should have a MoBagel account first.  
Please make sure you already have a MoBagel account. If not, please visit [here](http://app.mobagel.com/signup.php).

## Create product  
Your product is an essential part of the MoBagel platform. It's the type of your device, such as Smart Air Conditioner, Smart Lock or Robot Cleaner. For more information about [product](user-guide/introduction.md#product).  

Fill out the information of your product. *[Examples]  
   
 
 1. `Product Name` : Name of your Product [iConditioner1.0]
 2. `Product Brief` : Brief description of your Product [Smart air conditioner]
 3. `Product Description` : Detailed information about your Product  
 [Provide Wi-Fi, 3G/4G, Bluetooth 4.0. APP monitoring and remote control]

## Create a device  
Device is the basic unit of MoBagel platform. Each device should only belong to a single product, but a product can contain multiple devices. For more information about [device](user-guide/introduction.md#device).

1. Click on the Product you just created
2. Click `Create Now!`
3. Pull the bar to your right to choose how many devices you want to add, and click `Create`.  
 
After you completed creating devices, you can see the information of your devices on the Device List. If you want to take a look at the details, simply click on it. 

## Support Platform
Operating System: linux, ubuntu, debian

## Requirement
To install `MoBagel-C-SDK`, you need the following tools/libraries in your environment(linux base). 

```
sudo apt-get update && sudo apt-get install -y cmake libcurl4-openssl-dev g++
```

* [cmake](https://cmake.org/) - Build libmobagel library.
* [libcurl](https://curl.haxx.se/libcurl/) - perform HTTP/HTTPS.
 
## Installation
With a single command line, you can install MoBagel-C-SDK.
```
sh install.sh
```
## Example
The code sample below is to check if you successfully send a report or not. The response will also contain timestamp to synchronize device time.
```
./build/examples/main
```
Example Response:
```
Successfully register a device!
Server timestamp: 1457690569
Successfully send a report: {"message":"\"7\" must have a length greater than 64","timestamp":1457690569}
```
## Usage
These are the steps to send a report.   
1. Include header
```
#include <mobagel/mobagel.h>
```

2. Create MoBagel object with your product key
```
MoBagel *mobagel = new MoBagel("YOUR_PRODUCT_KEY");
```

3. (optional)If you have device key already, skip to 4. Register a new device.
```
string device_key = mobagel->registerDevice();
```

4. Create MoBagel client with device key. (Every device MUST need their own client)
```
MoBagelClient *client = new MoBagelClient(device_key);
```

5. Send report from device
```
MoBagelReport report;
report.state("normal");
report.custom("temperature", 123);
report.custom("pressure", 123.12);
report.custom("label", "test");
client->sendReport(report, report_callback);
```

## Full Example
```
#include <iostream>
#include <string>
#include <mobagel/mobagel.h>

using namespace std;

void time_callback(MoBagelResponse* res) {
    cout << "Time: ";
    res->print();
    cout << endl;
}

void report_callback(MoBagelResponse* res) {
    cout << "Report: ";
    res->print();
    cout << endl;
}

int main(int argc, const char * argv[]) {

    // create mobagel object
    string product_key = "1111111111222222222233333333334444444444555555555566666666667777";
    MoBagel *mobagel = new MoBagel(product_key);

    // register a device
    string device_key = mobagel->registerDevice();

    // create mobagel client
    MoBagelClient *client = new MoBagelClient(device_key);

    // get current timestamp
    client->getTime(time_callback);

    // send report from client
    MoBagelReport report;
    report.state("normal");
    report.custom("temperature", 123);
    report.custom("pressure", 123.12);
    report.custom("label", "test");
    client->sendReport(report, report_callback);

    return 0;
}

```

