# MoBagel-python-SDK   
Use MoBagel-python-SDK to quickly install MoBagel to your device(s). MoBagel-python-SDK is an open-source python library that makes it easy to integrate your python application with MoBagel. 

---

# Preparation
## Creating an account
If you do not have an account, please create an account [here](https://app.mobagel.com/signup). After you create an account, you will be directed to the dashboard.

## Creating a new product
To use MoBagel, you first have to create a `product`, which is essentially a group of same `devices`. You can create new products in the dashboard.

For example:  

[Product Name] iBulb  
[Product Brief] Smart light bulb  
[Product Description] Wi-Fi connected light bulb with motion sensors and temperature sensors.  

After you create a `product`, the system will generate a `product_key`, which will be used to create  `devices` later on.

## Locating your product key
After you create a `product`, the system will generate a `product_key`, which will be used to create `device` later on.
​
To find your `product_key`, go to Overview -> Product List -> Click on your product.

​---  

## Installation
To run the example project, clone the repo, or run pip install from the Example directory first.

* Install by PyPI
    `$ pip install mobagel-python-sdk`


## Register your first device
Once you generated a `product_key` from the dashboard, you can use the `product_key` and registerDevice function to register a device in your application. You will get a `device_key`.

    ## import package
    import pybagel

    ## create mobagel object
    client = pybagel.Client(product_key="1111111111222222222233333333334444444444555555555566666666667777")

    ## register a device
    device_key = client.registerDevice()


## Connecting custom properties or events
In your device application, you will need to prepare your report before sending it to MoBagel.

* Determining different states of your devices to send along with your report

        # example states

        "state": "normal"
        "state": "error"

* Adding custom properties or events with a key beginning with c_

        # example custom properties or events

        "c_temperature": 30
        "c_event": "turned_on"
* Deciding when to send reports (time, frequency, events)


## Sending first report
Once you connect the sensor properties, you can generate a report with the sendReport function.  
You need `device-key` to send a report.  

    # sample report
    report_content = {
        "state": "normal",
        "c_humidity": 30,
        "c_function": "humidify" ,
        "c_temperature": 80
    }

    client.sendReport(device_key, report_content)
