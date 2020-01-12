# Arlec - Grid Conenct GLD110HA Plug (TYWE3L)
Model purchased from Bunnings Aus for AUD$27 in a kit of 2 globes and 2 smart plugs

![Image](./images/device.jpg?raw=true)

Smart Globe with CWWW and brightness control, based in ESP8266.

![Image](./images/globe_inside.jpg?raw=true)

![Image](./images/globe_ledarray.jpg?raw=true)

Device has inbuilt gamma correction and brightness control IC BP5926. Standard ESPHome CWWW platform will not work with it.

I created a custom light output to work with ESPhome and its temperature slider. Please see below for a difference on how these glbs operate vs standard CWWW.

![Image](./images/CustomLightWork.png?raw=true)


## Installation

Use the arlec_gld110ha_grid_connect_globe_1.yaml file to build your ESPHome config file.

Place CWWWSinglepintempandbrightnessLightOutput.h into your /config/ESPhome directory

Update the following fields in the yaml file;
```bash

Line 16: devicename: arlec_gld110ha_grid_connect_globe_1 ** This is what you want to call your ESPHome node **
Line 18: upper_devicename: Arlec GLD110HA Globe ** This is what you want to call your ESPHome node **

Line 24:  esp8266_restore_from_flash: true ** This will kill the ESP if your using it for high occurance changes (Disco mode) with this enabled, see https://esphome.io/components/esphome.html#esphome-esp8266-restore-from-flash **

Line 28: wifi:
Line 29:  ssid: "SSID" ** Change this to your Wifi SSID **
Line 30:  password: "PASSWORD" ** Change this to your Wifi password**

Line 33  ap:
Line 35    password: "PASSWORD"  ** Change this to your emergency AP password**
If you do not want the fallback hotspot remove lines 23-28

# Enable Home Assistant API
Line 44: api:
Line 45:   password: "PASSWORD" ** Change this to your ESPHome API password**
Line 47: ota:
Line 48:   password: "PASSWORD" ** Change this to your ESPHome ota password**

Line 59: #restore_mode: ALWAYS_ON ** Uncomment this line IF your not using the restore from flash, otherwise when you turn the light on it won't turn the LED on. **

Line 64: pin: GPIO13  ** If different pin for light temperature change it here **
Line 64: pin: GPIO5   ** If different pin for brightness change it here **

```