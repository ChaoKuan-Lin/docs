# C SDK

## Get an account
To use MoBagel API, you should have a Bagel Account fitst.

Please make sure you already have a MoBagel account. If not, please visit [here](http://app.mobagel.com/signup.php).

## Create an product

## Create a device

## Requirements

# libmobagel

### Requirement
To install *libmobagel*, you need the following tools/libraries in your environment :

* [cmake](https://cmake.org/) - Build libmobagel library.
* [libcurl](https://curl.haxx.se/libcurl/) - perform HTTP/HTTPS.
 
### Installation
```
$ mkdir build
$ cd build
$ cmake ..
$ make
$ make install
```

### Usage
1. Include header
```
#include <mobagel/mobagel.h>
```

2. Create MoBagel object with product key
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

### Full Example
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

