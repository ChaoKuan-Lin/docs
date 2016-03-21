# MoBagel C SDK
Use MoBagel C SDK to quickly install MoBagel to your device(s). MoBagel C SDK is an open-source C library that makes it easy to integrate your C application with MoBagel. 


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

* Linux
* ubuntu
* debian
​

## Requirement
To install `MoBagel C SDK` on your device, you need the following tools/libraries in your Linux based environment. 

* [gcc](https://gcc.gnu.org) - GNU C Compiler.
* [cmake](https://cmake.org/) - Build libmobagel library.
* [libcurl](https://curl.haxx.se/libcurl/) - perform HTTP/HTTPS.
 
If do you not have these tools/libraries, `MoBagel C SDK` will install these for you.

## Installing SDK

```
$ git clone https://github.com/MOBAGEL/mobagel-c-sdk.git
```

or [download directly from GitHub](https://github.com/MOBAGEL/mobagel-c-sdk)

```
$ cd mobagel-c-sdk
$ sudo ./install.sh
```

## (Optional) Running sample test 

To check whether you the SDK has been installed successfully, run the following code:

```
$ ./build/examples/main
```

If you see the following response, congratulations! You have successfully installed the SDK.

```
Successfully register a device!Server timestamp: 1458016398
Successfully send a report: {"data":"56e790d2f8e9d32dc28b4567","timestamp":1458016399}
```

---
# Example Walkthrough

## Full Example

Located in /examples/main.cpp

```
// main.cpp

// Include header
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
    // every device MUST need their own client
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
// send report from client
MoBagelReport report;
report.state("normal");
report.custom("temperature", 123);
report.custom("pressure", 123.12);
report.custom("label", "test");
client->sendReport(report, report_callback);
```

## Compiling the application
After you set up your application, you will need to run the following commands to make the changes:

```
$ sudo ./install.sh
$ ./build/examples/main
```

If you receive the following response, then your request has been successfully sent to MoBagel and your registered device and report will appear in your MoBagel dashboard.

```
Successfully register a device!Server timestamp: 1458016398
Successfully send a report: {"data":"56e790d2f8e9d32dc28b4567","timestamp":1458016399}
```
