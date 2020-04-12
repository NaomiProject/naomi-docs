---
id: controlled
label: ControlLED
title: ControlLED - Speechhandler
type: speechhandlers
description: "A really simple module that combine Naomi and the Arduino platform to show possibilities in IOT and new interactions."
logo: images/plugins/led.png
source: https://github.com/NaomiProject/controlLED-plugin/edit/master/README.md
meta:
  - property: og:title
    content: "ControlLED - Speechhandler"
  - property: og:description
    content: "A really simple module that combine Naomi and the Arduino platform to show possibilities in IOT and new interactions."
---


# Control LED - Speechhandler

<PluginLogo/>

>:warning: Note: Here's an example of a plugin package for Naomi providing basics information about the plugin such as: language and the version support, include others specific files (i.e. provide your Arduino code) and instructions...

> This should be used as a generic template 

A really simple module that combine Naomi and the Arduino platform to show possibilities in IOT and new interactions.

With this really simple plugin you can basically control 2 leds using your voice.

* **Languages:** _English and French_
* **Naomi version support:** _V2.1_

* **dependencies:** [pyserial](https://pypi.org/project/pyserial/)

## Installation

:warning: **first make sure you have the necessary dependencies to run it**

To install this plugin in Naomi **using terminal**: 

**1.** Open a terminal window and go in the speechandler plugin folder:

`cd your_naomi_installation_directory/plugins/speechhandler`

**2.** and then clone the plugin from GitHub to your `speechhandler` folder

`git clone https://github.com/NaomiProject/controlLED.git`

**3.** compile the translations if you need to:

`~/Naomi-1/./compile_translations.sh`

**4.** Upload the arduino code available in `/controlLED/arduino_code` in the board

**5.** and then launch Naomi ! H

Have fun :wink:

**Need help ? we have a [discord](https://discord.gg/knequ9t) server for support**

## Arduino setup

* **IDE version:** _1.8.5_
* **Arduino board:** _Any (Nano for the example below)_

### Wiring 

Using digital PIN 2 for the green led and digital pin 6 for the red led

![Image not available for now, please contact support on discord](https://github.com/NaomiProject/controlLED/blob/master/SerialTest.png)

### Error

* could not open port

Naomi tries both '/dev/ttyACM0' and '/dev/ttyUSB0' to search for your Arduino. If
your Arduino has been assigned to a different device name in linux (such as
'/dev/ttyACM1') you can put the device name in profile.yml:

```
Control LED:
    device: '/dev/ttyACM1'
```

**Need help ? we have a [discord](https://discord.gg/knequ9t) server for support**

<EditPageLink/>