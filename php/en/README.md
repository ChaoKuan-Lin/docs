# mobagel-php-sdk
mobagel sdk for PHP

## Install
`composer install mobagel/mobagel-php-sdk`

## Usage
```
<?php

require 'vendor/autoload.php';

$config = [
    "product_id" => "YOUR_PRODUCT_ID",
    "product_key" => "YOUR_PRODUCT_KEY",
    "device_id" => "YOUR_DEVICE_ID",
    "device_key" => "YOUR_DEVICE_KEY",
];

$client = new MoBagel\MoBagelClient($config);

$contents = [
    "state" => "normal",
    "c_custom" => "foo",
]

$ret = $client->sendReport($contents);

print_r($ret);

```
