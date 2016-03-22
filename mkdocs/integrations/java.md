# MoBagel Java SDK   
Use MoBagel Java SDK to quickly install MoBagel to your device(s). MoBagel Java SDK is an open-source java library that makes it easy to integrate your java application with MoBagel. 


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
## Installing SDK
You can install MoBagel Java SDK from [HERE.](GitHubhttps://github.com/MOBAGEL/mobagel-java-sdk/blob/master/mobagel-sdk.jar)

---
# Example Walkthrough
## Full Example
```java
import org.mobagel.MoBagelClient;
import org.mobagel.MoBagelDevice;
import org.mobagel.MoBagelHandler;
import java.util.HashMap;

final MoBagelClient client = new MoBagelClient("1111111111222222222233333333334444444444555555555566666666667777");
final MoBagelHandler handler = new MoBagelHandler() {

   @Override
   public void registerHandler(int code, String data) {
       System.out.printf("HTTP code: %d, device-key: %s %n", code, data);

       final String key = data;
       MoBagelDevice device = new MoBagelDevice(key);
       final HashMap map = new HashMap<>();
       map.put("state", "Put your device state here"); // (mandatory)
//    map.put("custom-key-with-prefix-c_" , "custom-field"); //(optional)
       device.report(map, this);
   }

   @Override
   public void APIHandler(int code, String data) {
       System.out.printf("HTTP code: %d, report response: %s %n", code, data);
   }

   @Override
   public void ExceptionHandler(int code, Error error) {
       System.out.printf("HTTP code: %d, Error msg: %s %n", code, error.getMessage());
   }
};

client.register(handler);
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
MoBagelDevice device = MoBagelDevice(key);
final HashMap map = new HashMap<>();
map.put("state", "Put your device state here"); // (mandatory)
//map.put("custom-key-with-prefix-c_" , "custom-field"); //(optional)
device.report(map, this);
```