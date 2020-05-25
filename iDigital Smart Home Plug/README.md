# iDigital Smart hbome WIFI Power Plug with USB Port

Yes what a great name :|, from here on I will call it the iDigital Smart Plug

Model purchased from Reject Shop Australia on sale for AUD$9

![Image](./images/device.jpg?raw=true)

Simple single plug, with 1.5A non switchable USB port.

Top PCB:

![Image](./images/PCBtop.jpg?raw=true)

Rear PCB:

![Image](./images/PCBrear.jpg?raw=true)

Device has Dual relays, one GPIO triggers both.

Device has red and blue LEDs, blue LED is automatically switched on and cannot be turned off. Red on GPIO 14, purple if you dont invert red LED.

Internal module has no branding but is flashed with generic Tuya (even the app is native tuya). It is actually an ESP8266-S3 ([datasheet](./images/ESP8266-S3_WiFi_Module_Datasheet.pdf) )

Pinout:

![Image](./images/pinout.png?raw=true)

Thanks to gn0st1c for this simple pinout graphic; https://github.com/xoseperez/espurna/issues/1502#issuecomment-456255987

And if we orientate the PCB correctly you can see the pin out for this plug.

![Image](./images/PCBclose.jpg?raw=true)



## Installation

Use the idigital_smart_plug.yaml file to build your ESPHome config file.

Update the following fields;
```bash
Line 11: devicename: idigital_smart_plug ** This is what you want to call your ESPHome node **

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
