# Authentication

## Overview
In the MoBagel platform, the only way to communicate with the device is having both the `product_key` and `device_key`. If you want to control other devices simultaneously, we provide a master-slave mechanism to help handle your requests. Each device has its masters and slaves. Devices can control or receive information from their slaves, and on the other hand, devices can be controlled by their masters.

> **Notice**  
> The master-slave mechanism can only be defined by setting the masters of each device. You cannot define the slaves of each device. Once masters are defined, masters can control its slave devices.

## Examples
1. There are two devices, M0 and D0. Assume that they have the same `product_id`. If M0 wants to send a command to D0, D0 should set M0 as its master first.  
![authentication-1](../../img/docs/authentication-1.png)
2. There are three devices, M0, D0 and D1. Assume that D0 and D1 do not have the same Product Id. If M0 wants to send command to D0 and D1, M0 should have two `product_key` and `device_key`. One is for D0, and the other one is for D1. Then, D0 and D1 should set M0 as their master respectively.  
![authentication-2](../../img/docs/authentication-2.png)