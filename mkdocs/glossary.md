
# Glossary
---
###`custom property`    
Customize sensor properties. You can include various sensor properties in your report. Take smart air conditioner as an example, temperature and humidity might be your custom properties. 

---
###`device`  
Each device should only belong to a single product, but a product can contain multiple devices. You can use the `product_key` and `registerDevice` function to register a device in your application.

---
###`device key`   
A 64 bytes unique immutable identifier. Key of a device. You will get the `device_key` when you register your device. Each device has only one `device_key`. You use it to send reports. MoBagel system uses device key to do authentication.   

---
###`product`  
Device group. One product will have many devices. It's the type of your device. Such as Smart light bulb, Smart air conditioner or Smart Lock. You can create new products on the dashboard. Once you create a product, the system will generate a `product_key`. 
 
---
###`product key`   
A 64 bytes unique immutable identifier. Key of the product. Each product has only one `product_key`. After you create a product, the system will generate a `product_key`, which will be used to create devices.

---
###`report`  
Sensor data from the device. Includes all kinds of sensor property. You must include state, latitude and longitude in the report. Other custom states(e.g., temperature, humidity, mode) are optional. More information about report.

---
###`state`   
The status of the device. Must included in the report. For example, you can set "Normal", "Error" for smart air conditioner. 