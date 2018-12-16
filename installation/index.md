---
title: Installation Overview
source: https://github.com/naomiproject/naomi-docs/blob/master/installation/index.md
meta:
  - property: og:title
    content: "Installation Overview"
  - property: og:description
    content: an open source platform for developing always-on, voice-controlled applications
---

# Installation Overview

Naomi is based on the Jasper framework and is fully written in Python.
As such, it only depends on a python installation, which is available for many platforms.
Naomi can be executed on different versions of **macOS** and **Windows** and many different variants of **Linux** (Ubuntu, Raspbian, ...).

Please be aware of the fact, that Naomi is based on a new base and introduces new concepts.
Therefore, tutorials and help you may find on the internet for Jasper **might** be outdated!

## Platform Recommendations

1. You are **new to Naomi** and want to give it a try? You are in luck:
    - Set up Naomi on your local RPI in just a few steps.

2. You gained some experience and want to use Naomi as a total vocal assistant?
    Typical hardware and software requirements are:
    - **24/7 availability:** A dedicated system connected by Ethernet and running continuously.
    - **Energy and space efficient:** A device capable of performing the task at hand without being exaggerated
    - **Extendibility:** Your system should be capable of running additional software like an MQTT broker or a persistence and graphing software.
    - **Peripherals:** Depending on your home automation hardware, you will need additional  peripheral devices such as a WiFi interface or a special USB radio module.

Many devices are suited to host a continuous installation of Naomi.
Experiences with different devices and environments can be found in the [community forum hardware section](https://community.projectnaomi.com/c/hardware/server).

The [Raspberry Pi](rasppi.html) is quite popular, especially as we offer a quick setup with [Naobian](naobian.html).
A popular alternative is [our solution for the Synology DiskStation](synology.html), which many users already own in their homes.
The previously mentioned [Naobian](naobian.html) can also be used to kickstart your Naomi experience on existing Debian/Ubuntu based Linux systems.

Please check the menu to the left for all available options.

## Prerequisites

Due to the way we have sturtured the setup of Naomi, there are no software prerequisites (Naomi handles all of that for you!). All you need to run Naomi is compatable hardware/os.

## Setup variants

Before you can start, three decisions have to be made:

1. Naomi is available as a platform independent archive file or through a package repository:
    - **Manual setup:** Download and extract a platform independent zip archive: [macOS](macos.html), [Windows](windows.html), [Linux](linux.html#manual-installation)
    - **Package setup:** Install though a package repository, including automatic updates.
    This option is only available for Debian or Ubuntu derivatives and the recommended choice: [Linux (apt/deb)](linux.html#package-repository-installation)

2. Stable release or cutting edge:
    - **Stable:** Use the latest official release ([hosted on Bintray](https://bintray.com/naomiproject/mvn/naomi-distro)).
    - **Snapshot:** Benefit from the latest changes in the daily created snapshot ([hosted on #](https://#)).

## Installation

Please follow the instructions in the installation article matching your platform (see the menu to the left).

## Additional Steps

After you got Naomi set up and running, there are a few additional setup steps you should consider:

- Configure a network share on your Naomi host device and mount it locally: [Linux Samba Share](linux.html#network-sharing), Windows file sharing, ...

- Install [Visual Studio Code](https://code.visualstudio.com/Download) and the [Naomi VS Code Extension](../configuration/editors.html#naomi-vs-code-extension) on your local machine, to manage your (remote) configuration files.
    The Naomi VS Code Extension comes with built-in support for the Naomi syntax and elements.

## Help

The very active [Naomi Community Forum](https://community.projectnaomi.com) provides many more details and hints.
If you run into any problems, use the search function or open a new thread with your detailed question.

<DocPreviousVersions/>
<EditPageLink/>
