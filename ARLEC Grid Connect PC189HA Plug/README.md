# Arlec - Grid Connect PC189HA Plug (TYWE2S)
Model purchased from Bunnings Aus for AUD$27 in a kit of 2 globes and 2 smart plugs

![Image](./images/device.jpg?raw=true)

Simple single plug.

![Image](./images/PCB.jpg?raw=true)

Internal module Tuya TYWE2S, Image copied from Jason Lewis blog https://emacstragic.net/2019/07/23/putting-esphome-on-arlec-smart-plug-in-socket/ 

Device has Dual relays, one GPIO triggers both.

Device has red and blue LEDs, when both are on you get purple.





## Installation

Use the arlec_pc189ha_plug.yaml file to build your ESPHome config file.

Update the following fields;
```bash
Line 11: devicename: arlec_pc189ha_plug ** This is what you want to call your ESPHome node **

Line 20: wifi:
Line 21:  ssid: "SSID" ** Change this to your Wifi SSID **
Line 22:  password: "PASSWORD" ** Change this to your Wifi password**

Line 25  ap:
Line 27    password: "PASSWORD"  ** Change this to your emergency AP password**
If you do not want the fallback hotspot remove lines 23-28

# Enable Home Assistant API
Line 39: api:
Line 40:   password: "PASSWORD" ** Change this to your ESPHome API password**
Line 42: ota:
Line 43:   password: "PASSWORD" ** Change this to your ESPHome ota password**

```