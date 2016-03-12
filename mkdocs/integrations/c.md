# MoBagel-C-SDK   
Get started quickly using MoBagel service with the MoBagel-C-SDK. The SDK is a modern, open-source C library that makes it easy integrate your C application with MoBagel service. 

[Download the MoBagel-C-SDK](https://github.com/MOBAGEL/mobagel-c-sdk)

## Set up your account
To use MoBagel API, you should have a MoBagel account first.  
Please make sure you already have a MoBagel account. If not, please visit [here](http://app.mobagel.com/signup.php).

## Create product  
To use MoBagel, you first have to create a `product`, which is essentially a group of same `device`. You can create new products in the dashboard. 

For example:     

 * [Product Name] iBulb
 * [Product Brief] Smart light bulb
 * [Product Description] Wi-Fi connected light bulb with motion sensors and temperature sensors.

After you create a `product`, the system will generate a `product_key`, which will be used to create `device` later on.

## Register your first device

Once you generated a `product_key` from the dashboard, you can use the `product_key` and `registerDevice` function to register a `device` in your application.

```

    // create mobagel object
    string product_key = "1111111111222222222233333333334444444444555555555566666666667777";
    MoBagel *mobagel = new MoBagel(product_key);

    // register a device
    string device_key = mobagel->registerDevice();

```

## Support Platform
Operating System: linux, ubuntu, debian

## Requirement
To install `MoBagel-C-SDK`, you need the following tools/libraries in your environment (linux base). 


* [gcc](https://gcc.gnu.org) - GNU C Compiler.
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

  1) Include header

```
#include <mobagel/mobagel.h>
```

  2) Create MoBagel object with your product key

```
MoBagel *mobagel = new MoBagel("YOUR_PRODUCT_KEY");
```

  3) Register a new device (optional: if you have device key already, skip to 4).

```
string device_key = mobagel->registerDevice();
```

  4) Create MoBagel client with device key. (Every device MUST need their own client)

```
MoBagelClient *client = new MoBagelClient(device_key);
```

  5) Send report from device

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

