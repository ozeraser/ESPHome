# Bauhn - Connected ASPU-1019 Plug (TYWE2S)
Model purchased from ALDI Aus for AUD$9.99

![Image](./images/device.jpg?raw=true)

Wifi Plug with dual USB 2.4A, based in ESP8266.

![Image](./images/pluginside.jpg?raw=true)

Device has Dual relays one on active and one on neutral. Both need to be active to turn items plugged in on.

![Image](./images/LA_WF3_08.png?raw=true)

Internal module Tuya TYWE2S



## Installation

Use the bauhn_aspu_1019_plug.yaml file to build your ESPHome config file.

Update the following fields;
```bash
Line 10: devicename: bauhn_aspu_1019_plug ** This is what you want to call your ESPHome node **

Line 19: wifi:
Line 20:  ssid: "SSID" ** Change this to your Wifi SSID **
Line 21:  password: "PASSWORD" ** Change this to your Wifi password**

Line 24  ap:
Line 26    password: "PASSWORD"  ** Change this to your emergency AP password**
If you do not want the fallback hotspot remove lines 23-28

# Enable Home Assistant API
Line 38: api:
Line 39:   password: "PASSWORD" ** Change this to your ESPHome API password**
Line 41: ota:
Line 42:   password: "PASSWORD" ** Change this to your ESPHome ota password**

```