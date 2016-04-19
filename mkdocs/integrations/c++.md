# MoBagel C++ SDK
Use MoBagel C++ SDK to quickly install MoBagel to your device(s). MoBagel C++ SDK is an open-source C++ library that makes it easy to integrate your C++ application with MoBagel. 


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

---
# Installation

## Supported Platform

* Linux
* ubuntu
* debian
​

## Requirement
To install `MoBagel C++ SDK` on your device, you need the following tools/libraries in your Linux based environment. 

* [gcc](https://gcc.gnu.org) - GNU C++ Compiler.
* [cmake](https://cmake.org/) - Build libmobagel library.
* [libcurl](https://curl.haxx.se/libcurl/) - perform HTTP/HTTPS.
 
If do you not have these tools/libraries, `MoBagel C++ SDK` will install these for you.

## Installing SDK

```
$ git clone https://github.com/MOBAGEL/mobagel-cpp-sdk.git
```

or [download directly from GitHub](https://github.com/MOBAGEL/mobagel-cpp-sdk)

```
$ cd mobagel-cpp-sdk
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
string product_key = "{YOUR_PRODUCT_KEY}";
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
