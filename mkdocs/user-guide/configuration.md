# Configuration

## Overview

Since there are lots of IoT devices, MoBagel offers many different ways to communicate with your devices. This section will demonstrate how to configure your requests and also customize your demands to fit the needs of your devices.

## Protocol
MoBagel supports two kinds of common protocols `HTTP` and `HTTPS` to communicate with the platform. You can choose the protocol based on your devices.

*More information about [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) and [HTTPS](https://en.wikipedia.org/wiki/HTTPS).*

For `HTTP`:
```http
port: 80
endpoint: http://api.mobagel.com
```

For `HTTPS`:
```http
port: 443
endpoint: https://api.mobagel.com
```
## Encryption
As an additional layer of security, we provide two ways of encryption, `AES128` and `AES256`. If you use `HTTP`, it is highly suggested that you encrypt your data.

*More information about [AES](https://de.wikipedia.org/wiki/Advanced_Encryption_Standard).*

**Please follow the steps below to encrypt your data.**

#### Generate AES Keys.

AES keys are used to encrypt and decrypt data. AES keys are generated using Secure Hash Algorithm (SHA). For security purposes, the encrypt key and the decrypt key are different and generated separately as below:

For `AES128

    encrypt key = SHA128(device_key:timestamp)
    decrypt key = SHA128(device_key)

For `AES256

    encrypt key = SHA256(device_key:timestamp)
    decrypt key = SHA256(device_key)

**Notice:** `device_key` and `timestamp` are concatenated with colons

*More information about [SHA](https://en.wikipeorg/wiki/Secure_Hash_Algorithm)*


#### Add Header.

Put `Encrypt: AES128` or `Encrypt: AES256` into your http header. Only accept `AES128` or `AES256`. If you do not want to encrypt data, leave the encryption field empty.

#### Encrypt POST data

> If you use `GET` method, please skip this step.

Suppose your plain post data is:
```json
{
    "data": {
        "state": "FATAL_ERROR",
        "latlng": "23.23:-21.12"
    }
}
```
Use the encrypt key that you just generated and take the corresponding AES type to encrypt your data.

For `AES128`

    aes_encrypted_data = encrypt('AES128', encrypt_key, data)

For `AES256`

    aes_encrypted_data = encrypt('AES256', encrypt_key, data)

After encrypting, you will receive an encrypted byte string. Please encode it by `Base64`. Then, your post data is completely encrypted.

*More information about [Base64](https://en.wikipedia.org/wiki/Base64)*

    encrypted_post_data = base64_encode(aes_encrypted_data)

The encrypted post data will look like:
```json
{
    "data": "d0VxZndlcWZ2MzRnM2c="
}
```


#### Decrypt Response Data
To decrypt post data, you have to use `Base64` to decode first.
Then, use the decrypt key to decrypt your response data.

Base64 Decode

    response_encrypted_data = base64_decode(response_encoded_encrypted_data)

For `AES128`

    response_data = decrypt('AES128', decrypt_key, response_encrypted_data)

For `AES256`

    response_data = decrypt('AES256', decrypt_key, response_encrypted_data)

### Flow

![encrypt](../../img/docs/encrypt.png)