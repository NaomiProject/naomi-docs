---
title: Raspberry Pi
source: https://github.com/naomiproject/naomi-docs/blob/master/installation/rasppi.md
meta:
  - property: og:title
    content: "RaspberryPi Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Raspberry Pi

Because of its **low price**, its **small form factor** and the **low energy consumption**, the [Raspberry Pi](https://www.raspberrypi.org) is a quite popular platform for Naomi.
It is favored amongst existing users and a recommended choice for newcomers.

![Raspberry Pi 2 Model B](./system/rpi2b.png)

If you want to learn more about the possibilities of the Raspberry Pi and Linux in general, many tutorials can be found on the internet.
These including the official [raspberrypi.org help articles](https://www.raspberrypi.org/help) or the in-detail articles at [eLinux.org](http://elinux.org/RPi_Tutorials).

Recommendations for a ["headless"](https://en.wikipedia.org/wiki/Headless_computer) hardware setup:


- [Raspberry Pi 3 Model B+](https://www.raspberrypi.org/products/raspberry-pi-3-model-b-plus/).
- USB Microphone (Has been tested with [Akiro Kinobo USB Microphone](https://www.amazon.com/dp/B06XVXKDXC/))*
- [8GB SD Card](https://www.amazon.com/Sandisk-Ultra-Micro-UHS-I-Adapter/dp/B07GH5J77R)
- [Ethernet Cable](https://www.amazon.com/gp/product/B00N2VILDM/)
- [Airlink Mini-USB Adapter](https://www.amazon.com/Airlink101-AWLL5088V2-Wireless-Ultra-Adapter/dp/B00EE940IG) (optional — see below)
- [Micro-USB Cable](https://www.amazon.com/AmazonBasics-Male-Micro-Cable-Black/dp/B0711PVX6Z/)
- [USB Wall Charging Adapter](https://www.amazon.com/AmazonBasics-One-Port-USB-Wall-Charger/dp/B0773J79KC/)
- [Speakers that work through the Raspberry Pi audio jack (probably need to be self-powered)](https://www.google.com/shopping/product/1749789584867681205)

The [Raspberry Pi Verified Peripherals List](https://www.raspberrypi.org/products/) may be helpful for finding substitutes for the products recommended above.

> *note that other mics do work but have not been tested. A complete list of supported mics will be coming soon!

As mentioned above, the wireless adapter is optional. Naomi runs just fine on a wired connection (via ethernet), so you can choose between the two setups depending on what works best for you.

## Recommended Setup

We also provide a **preconfigured image** for the Raspberry Pi, with the latest build of Naomi and many useful software components.
The image provided by the **Naobian** projects is based on Raspbian and under constant improvement.

Check out more details about [Naobian, the hassle-free Naomi setup](naobian.html).

## Manual Setup

If you want or need to set up Naomi on a Raspberry Pi by yourself, please follow these recommendations.
For the beginning, we recommend to [download](https://www.raspberrypi.org/downloads/raspbian) and [install](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) the latest Raspbian SD card image.
You may choose the "Lite" version.

**Attention:**
As of the November 2016 release, Raspbian has the SSH server disabled by default.
You will have to enable it manually.
For headless setup, SSH can be enabled by placing a file named "ssh", without any extension, onto the boot partition of the SD card.

**Connecting:**
Get your SD card and network cable plugged in and power up.
Booting up takes up to 10 minutes.
To connect with an SSH client (like [Putty](https://www.raspberrypi.org/documentation/remote-access/ssh/windows.md)), you need to know the IP address or hostname of your device.
A standard Raspbian setup should be reachable either by the hostname "raspberrypi" or though the local domain name "raspberrypi.local".
If you are not able to connect, check your routers web frontend for newly connected devices.

**First Steps:**
Connected via SSH, execute the Raspbian configuration menu by running `sudo raspi-config`.
Go through the following steps:

- Expand the file system
- Change your password
- (Change the host name if you wish, e.g. "naomipi")
- Restart

As a good practice, run a full upgrade and install packages you like or need:

```shell
sudo apt-get update
sudo apt-get upgrade
```

**Note on Python:**
Raspbian in the latest full version already includes Python 2 and Python 3.
However, at the time of setup, the Naomi install updates and downloads both Python 2 & 3 just to be safe.

> Note: At the time of writing, the conversion to Python 3 has yet to happen on the stable release but the Milestone builds has been updated)

**Installation:**
Follow the Config [Documentation](/docs/configuration/) to setup the [Audio Engine](/docs/configuration/audio.html), [Text-to-Speech](/docs/configuration/tts.html), & [Speech-to-Text](/docs/configuration/stt.html).
Finally install Naomi on your Raspberry Pi, just as it is described on the [download](/download/) page.

<DocPreviousVersions/>
<EditPageLink/>
