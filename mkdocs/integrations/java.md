# MoBagel Java SDK   
Use MoBagel Java SDK to quickly install MoBagel to your device(s). MoBagel Java SDK is an open-source java library that makes it easy to integrate your java application with MoBagel. 


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
## Installing SDK
You can install MoBagel Java SDK from [here.](https://github.com/MOBAGEL/mobagel-java-sdk/blob/master/mobagel-sdk.jar)

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

## Registering your first device

Once you generated a product_key from the dashboard, you can use the product_key and registerDevice function to register a device in your application.

```
    import org.mobagel.MoBagelClient;
import org.mobagel.MoBagelDevice;
import org.mobagel.MoBagelHandler;
import org.mobagel.json.JSONObject;

final String product_key = "YOUR_PRODUCT_KEY";
// Initialize a Client Instance by product_key
final MoBagelClient client = new MoBagelClient(product_key);

// Register a device_key by client
final MoBagelHandler handler = new MoBagelHandler() {

   @Override
   public void registerHandler(final int code, final JSONObject responseObject, final String device_key) {
      // Save device_key
   }

   @Override
   public void APIHandler(int code, JSONObject responseObject) {

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
MoBagelDevice device = new MoBagelDevice(key);
final HashMap map = new HashMap<>();
map.put("state", "Put your device state here"); // (mandatory)
//map.put("custom-key-with-prefix-c_" , "custom-field"); //(optional)
device.report(map, this);
```