# Getting Started

This short tutorial will walk you through the basic setups of your MoBagel account. These are the only steps you need to do.

 1. Sign up for an account  
 2. Login to the dashboard  
 4. Create your Product  
 5. Create your Device  
 6. Send a report of your Device   

---
## Sign up for an account
To use the MoBagel API, you will need a MoBagel Account. [Create an account](https://app.mobagel.com/signup).

---
## Login to the dashboard
Login with your MoBagel account.  
![login](../img/docs/login.png)

---
## Create a new Product
Your product is an essential part of the MoBagel platform. It's the type of your device, such as Smart Air Conditioner, Smart Lock or Robot Cleaner. For more information about [product](user-guide/introduction.md#product).  

Fill out the information of your product. *[Examples]  
   
 
 1. `Product Name` : Name of your Product [iConditioner1.0]
 2. `Product Brief` : Brief description of your Product [Smart air conditioner]
 3. `Product Description` : Detailed information about your Product  
 [Provide Wi-Fi, 3G/4G, Bluetooth 4.0. APP monitoring and remote control]

![add-product](../img/docs/add-product.gif)

---
## Create a new Device
Device is the basic unit of MoBagel platform. Each device should only belong to a single product, but a product can contain multiple devices. For more information about [device](user-guide/introduction.md#device).

1. Click on the Product you just created
2. Click `Create Now!`
3. Pull the bar to your right to choose how many devices you want to add, and click `Create`.  
 
After you completed creating devices, you can see the information of your devices on the Device List. If you want to take a look at the details, simply click on it. 
![device-section](../img/docs/add-device.gif)

---
## Send a report of your Device

To send a report, there are little steps to do:

1. Prepare your Device Key
2. 


\\
 

    Assume that your device id is `D001`.

    To get your device information, your sample request will be:

    + Host: `https://api.mobagel.com/products/A001/devices/D001/reports`
    + Header: 

            Device-Id: D001

    + Body:

            {
                "data":
                {
                    "state": "normal",
                    "latitude": 12.321, 
                    "longitude": -32.12 
                }
            }

    *For more information about body, please see [introduction](user-guide/introduction.md)*

    You will receive a sample response like this:

        HTTP/1.1 201 CREATED
        Date: Mon, 26 Oct 2015 07:48:06 GMT
        Content-Length: 81
        Connection: keep-alive
        Content-Type: application/json
        Server: nginx/1.4.6 (Ubuntu)

        {
            "code": 201,
            "message": "success",
            "data": "$reportId"
        }

    > *You can send your sample request [here](https://apigee.com/console/others)*


