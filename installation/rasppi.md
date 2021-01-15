---
title: Raspberry Pi
source: https://github.com/naomiproject/naomi-docs/blob/dev/installation/rasppi.md
meta:
  - property: og:title
    content: "RaspberryPi Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Raspberry Pi

Because of its **low price**, **small form factor** and the **low energy consumption**, the [Raspberry Pi](https://www.raspberrypi.org) is a quite popular platform and thats no different for Naomi.
It is favored amongst existing users and a recommended choice for newcomers.

![Raspberry Pi 4 Model B](./system/rpi4b.png)

If you want to learn more about the possibilities of the Raspberry Pi and Linux in general, many tutorials can be found on the internet.
These including the official [raspberrypi.org help articles](https://www.raspberrypi.org/help) or the in-detail articles at [eLinux.org](http://elinux.org/RPi_Tutorials).

Recommendations for a ["headless"](https://en.wikipedia.org/wiki/Headless_computer) hardware setup:

- [Raspberry Pi 3 Model B+](https://www.raspberrypi.org/products/raspberry-pi-3-model-b-plus/).
- USB Microphone (Has been tested with [Akiro Kinobo USB Microphone](https://www.amazon.com/dp/B06XVXKDXC/)) but should work with just about any USB microphone*
- [8GiB SD Card](https://www.amazon.com/Sandisk-Ultra-Micro-UHS-I-Adapter/dp/B07GH5J77R) (16GiB recommended if you would like to play with DeepSpeech and/or Kaldi)
- [Ethernet Cable](https://www.amazon.com/gp/product/B00N2VILDM/)
- [Airlink Mini-USB Adapter](https://www.amazon.com/Airlink101-AWLL5088V2-Wireless-Ultra-Adapter/dp/B00EE940IG) (optional — see below)
- [Micro-USB Cable](https://www.amazon.com/AmazonBasics-Male-Micro-Cable-Black/dp/B0711PVX6Z/)
- [USB Wall Charging Adapter](https://www.amazon.com/AmazonBasics-One-Port-USB-Wall-Charger/dp/B0773J79KC/)
- [Speakers that work through the Raspberry Pi audio jack (probably need to be self-powered)](https://www.google.com/shopping/product/1749789584867681205)

The [Raspberry Pi Verified Peripherals List](https://www.raspberrypi.org/products/) may be helpful for finding substitutes for the products recommended above.

> *note that just about any USB or HAT microphone will work. Getting good audio quality is very important for Naomi to be able to hear you clearly (it can't read lips -- yet). Using a USB webcam with an integrated microphone is a good choice since it includes both clear, far field listening and the possibility of giving your Naomi sight. A conference phone that includes both a speaker and microphone and some noise cancellation between them is also a good choice that can reduce the tangle of wires around your Raspberry Pi.

As mentioned above, the wireless adapter is optional. Naomi runs just fine on a wired connection (via ethernet)
and does not require an always on connection to the internet. The wireless adapter allows you to access the
Raspberry Pi from another computer.

## Recommended Setup

We also provide a **preconfigured image** for the Raspberry Pi, with the latest build of Naomi and many useful software components.
The image provided by the **Naobian** project is based on Raspbian and under constant improvement.

Check out more details about [Naobian, the hassle-free Naomi setup](naobian.html).

## Manual Setup

If you want or need to set up Naomi on a Raspberry Pi by yourself, please follow these recommendations.
For the beginning, we recommend to [download](/download/) and [install](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) the latest Raspbian SD card image.
You may choose the "Lite" version.

**Attention:**
As of the November 2016 release, Raspbian has the SSH server disabled by default.
You will have to enable it manually.
For headless setup, SSH can be enabled by placing a file named "ssh", without any extension, onto the boot partition of the SD card.

**Connecting:**
Get your SD card and network cable plugged in and power up.
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
However, at the time of setup, the Naomi install updates and downloads Python just to be safe.

**Installation:**
To get Naomi up and running all you need to do is follow the steps described on the [download](/download/) page for RaspberryPi and the version you would like to use.

<DocPreviousVersions/>
<EditPageLink/>
