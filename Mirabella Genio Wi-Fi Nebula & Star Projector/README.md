# Mirabella Genio Wi-Fi Nebula & Star Projector

This is a ESP-12E / ESP-12F (I used a spare TYWE3S from a dead LED globe) chip swap as this projector is using the WB3S MCU

Model purchased from Kmart Australia on for AUD$69

![Image](./images/device.jpg?raw=true)

FIRSTLY FLASH YOUR ESP-12E or 12F with nodemcu or some other firmware that lets you upload firmware in the future. My TYWE3S was tuya so i just used tuya convert on it.

The device has 4 sticky feat you can peel off to find the phillips screw. Carefully unplug all the cables on the PCB.

Underside of PCB should look like:

![Image](./images/PCB_old_bottum.jpg?raw=true)

Top side should look like this:

![Image](./images/PCB_old_top.jpg?raw=true)

So good news is the ESP-12E or ESP-12F is the same pin out. Bad news is you need to desolder the old chip without breaking the tracks on the PCB, so if you havent done this before grab some solder braid and watch some youtube videos.

![Image](./images/PCB_replaced_with_esp.jpg?raw=true)

Now thanks to Jobbel https://github.com/Jobbel/SmartStarProjector-ESP-Mod who had done a similar activity for finding out what resistors are not needed.

So remove resistor R17, R18 and caoaitor C6 from the PCB as shown on the Image below (red box)

Use the salvaged R17,R18 or another 10k resistor to pull GPIO15 down to ground (yellow box), without this change the ESP8266 won't boot 

![Image](./images/hardware_changes.jpg?raw=true)

If you want you can pull the motor gearbox down and give it some additional grease here you can, but its most probably not needed.

Re-assemble ensuring the cables are put in the right slots and the right direction, also ensure no cables interfere with the cogs.

Pinout:

| ESP8266 GPIO | Function on the PCB|
| ------ | ------ |
| 4 | Red main LED |
| 12 | Green main LED |
| 14 | Blue main LED |
| 5 | Laser Motor |
| 13 | Rotation Motor |
| 15 | Blue status LED1 |
| 0 | Blue status LED2 |
| 16 | On/Off Button |


## Installation

Use the KMART_Mirabella_Genio_Nebula_Star_Projector.yaml file to build your ESPHome config file and upload to your ESP.

Update the following fields;
```bash
Line 5: name: 'rgb_stars' ** This is what you want to call your ESPHome node **
Line 6: device: 'rgb_stars' ** This is what you want to call your ESPHome node **

Line 17: wifi:
Line 18:  ssid: "SSID" ** Change this to your Wifi SSID **
Line 19:  password: "PASSWORD" ** Change this to your Wifi password**

Line 22  ap:
Line 24    password: "PASSWORD"  ** Change this to your emergency AP password**
If you do not want the fallback hotspot remove lines 22-24

# Enable Home Assistant API
Line 35: api:
Line 32:   password: 'your secret api password' ** Uncomment and change this to your ESPHome API password if required**
Line 42: ota:
Line 37:   password: 'your secret ota password' ** Uncomment and change this to your ESPHome ota password if requried**

```

## Light Features;

![Image](./images/roof.jpg?raw=true)

Laser intensity & Off
RGB intensity & Off
Motor Speed & Off
RGB Colour

These can be activated by HASS, OR the button on the side acts as a manual button to cycle through the effects.
I added a Random colour effect that doesnt change the brightness, and played with a bluey-greeny random effect (WIP)


## Display in HASS

Now if you havent already grab "https://github.com/thomasloven/lovelace-slider-entity-row" through HACS or manually, this will give you a nice component to play with.

![Image](./images/hass_display.PNG?raw=true)

Once you have that plugin working, Create a new "Entities" card, click "show code editor" and paste the following

```bash
type: entities
title: Nebula Lights
entities:
  - entity: light.rgb_stars_light
    name: Nebula Light
    toggle: true
    type: 'custom:slider-entity-row'
  - entity: light.rgb_stars_laser
    name: Nebula Laser
    toggle: true
    type: 'custom:slider-entity-row'
  - entity: light.rgb_stars_motor
    name: Nebula Motor
    toggle: true
    type: 'custom:slider-entity-row'
```

Now you should be good to go.

## Known issues;
Code is a bit of a mess of nested ifs, I will fix this in the future.
I have had an issue where i turn the motor off and the laser dims, I think there is some ground problem, but i assume it was from a bad desolder/resolder job.