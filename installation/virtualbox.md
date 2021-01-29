---
title: VirtualBox
source: https://github.com/naomiproject/naomi-docs/blob/dev/installation/virtualbox.md
meta:
  - property: og:title
    content: "VirtualBox Guild"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Naomi in Oracle VM VirtualBox

Installing Naomi on a virtual machine running on [Oracle Virtualbox](https://www.virtualbox.org) is a safe
and convenient way to try Naomi if you don't have a Raspberry Pi, don't use Linux on your computer, or just
want to make sure your computer configuration doesn't get changed.

We recommend using a Debian derivative of the Linux operating system for your guest OS, such as Raspberry Pi OS (formerly Raspbian), Ubuntu or Mint.

We are currently having an issue with portaudio and pulseaudio emptying out the audio buffer faster than Naomi can fill it,
leading to some buffer underflow errors when running Naomi in a VirtualBox guest.
For this reason, we recommend that you select "alsa" as your audio engine and "sysdefault-card-i82801aaich" as the default
device for both input and output when using a VirtualBox guest.
That way Naomi will use whatever you have set as the default input and output devices on your host system.

If you just want to try Naomi without having to install it yourself, you could download our Naobianx86 ova image.

Our VirtualBox image is built on Raspbian Buster x86, so is very similar to running Naomi on a Raspberry Pi.

The image is built to automatically log into the desktop as the "pi" user (password "raspberry") when you start it. There are
two icons on the desktop for Naomi and Naomi setup. Naomi setup just runs Naomi with the --repopulate flag. Naomi will run
out of the box, but using "Naomi Setup" to fill in other details like your location and time zone or give Naomi a custom name
will help you get the most out of your virtual assistant.

<DocPreviousVersions/>
<EditPageLink/>
