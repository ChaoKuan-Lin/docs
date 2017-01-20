# MoBagel PHP SDK   
Use MoBagel PHP SDK to quickly install MoBagel to your device(s). MoBagel PHP SDK is an open-source php library that makes it easy to integrate your PHP application with MoBagel. 

---

# Preparation

# Creating an account
If you do not have an account, please create an account [here](https://app.mobagel.com/login). After you create an account, you will be directed to the dashboard.
<img src="../../../img/MoBagel_Getting_Started/Sign_up.png" width="800">  

---
# Creating a new product
To use MoBagel, you first have to create a `product`, which is essentially a group of same `device`. You will be prompted to create a new product when you first enter the dashboard.

<img src="../../../img/MoBagel_Getting_Started/Enter_Product_name.png" width="800">  

After you create a `product`, you can go to **_Configuration -> Product Settings_** Info to retrieve your `product_key`, which will be used to create `device` later on.

<img src="../../../img/MoBagel_Getting_Started/Product_key.png" width="800">  

---
# Adding custom properties

<img src="../../../img/MoBagel_Getting_Started/Config_settings.png" width="200">   
In **_Product Settings_** under **_Configuration_**, you can add custom properties to your product.   
Custom properties should have the following requirements:   

<img src="../../../img/MoBagel_Getting_Started/Device_Settings.png" width="800">   

* **ID**:   
Property ID will always begin with `d_` (for numbers) or `s_` (for strings) to indicate that it is a custom property, this will be automatically asigned when you select a `Type`. Property IDs are unique and cannot repeat with itself.

* **Name**:   
You can set a custom name for each property. For example, if your ID is `d_012421`, you can set the name as `temperature`. The modules in the dashboard will display your property name instead of your property ID.

* **Type**:   
There are two types of properties: `number` and `string`.

**_Please note that you must configure your properties in your configuration before you send your first customized report._**


---
# Installation
## Requirement
You need to download [composer.](https://getcomposer.org/download/)

## Installing SDK
```
composer require mobagel/mobagel-php-sdk
```
or [download directly from GitHub](https://github.com/MOBAGEL/mobagel-php-sdk)

---
# Example Walkthrough
## Full Example

```
<?php
/**
 * MoBagel PHP SDK.
 *
 * @link      https://mobagel.com
 *
 * @copyright Copyright (c) 2017 MoBagel
 * @license   MoBagel Platform
 */
require 'vendor/autoload.php';
echo "This is MoBagel PHP SDK sample, you can learn how to `register device` and `report state` in this sample code\n";
// setup your product key
$productKey = "YOUR_PRODUCT_KEY";
$client = \MoBagel\MoBagel::Instance();
$client->setProductKey($productKey);
// register a new device
echo "Register device...";
$contents = [
    "s_string" => "phpSDK",
    "d_number" => 100
];
$response = $client->registerDevice($contents);
$body = $response->getBody()->getContents();
echo("Data response:\n");
print_r($body);
// send a report
echo "\nSend report...";
$object = json_decode($body);
$client->setDeviceKey($object->key);
$contents = [
    "s_category" => "phpSDK",
    "d_numeric" => 100
];
$response = $client->sendReport($contents);
$body = $response->getBody()->getContents();
echo("Data response:\n");
print_r($body);
```
