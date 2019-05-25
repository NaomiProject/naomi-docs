---
title: Installation Overview
source: https://github.com/naomiproject/naomi-docs/blob/dev/installation/index.md
meta:
  - property: og:title
    content: "Installation Overview"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Installation Overview

Naomi is based on the Jasper framework and is fully written in Python.
As such, it only depends on a python installation, which is available for many platforms.
Naomi can be executed on different versions of **macOS** and **Windows** and many different variants of **Linux** (Ubuntu, Raspbian, ...).

Please be aware of the fact, that Naomi is programmed on a new base and introduces new concepts.
Therefore, tutorials and help you may find on the internet for Jasper **WILL** be outdated!

## Platform Recommendations

1. You are **new to Naomi** and want to give it a try? You are in luck:
    - Set up Naomi on your local RPI in just a few steps.

2. More Coming Soon!

Many devices are suited to host a continuous installation of Naomi.
Experiences with different devices and environments can be found in the [community forum hardware section](https://community.projectnaomi.com/c/hardware/server).

The [Raspberry Pi](rasppi.html) is quite popular, especially as we offer a quick setup with [Naobian](naobian.html).
The previously mentioned [Naobian](naobian.html) can also be used to kickstart your Naomi experience on existing Debian/Ubuntu based Linux systems*.

>Note: *Offical Support Coming Soon!

Please check the menu to the left for all available options.

## Prerequisites

Due to the way we have sturtured the setup of Naomi, there are no software prerequisites (Naomi handles all of that for you!). All you need to run Naomi is compatable hardware/os.

## Setup variants

Before you can start, three decisions have to be made:

1. Naomi is available as a platform independent archive file or through a package repository:
    - **Manual setup:** Download and extract a platform independent zip archive: [RPI](rasppi.html), [macOS](macos.html), [Windows](windows.html), [Linux](linux.html#manual-installation)
    - **Package setup:** Install though a package repository, including automatic updates.
    This option is still in development as well as only available for Debian or Ubuntu derivatives and the recommended choice: [Linux (apt/deb)](linux.html#package-repository-installation)

2. Stable release or cutting edge found on the download page:
    - **Stable:** Use the latest official release .
    - **Snapshot:** Benefit from the latest changes in the daily created snapshot.

## Installation

Please follow the instructions in the installation page matching your platform (see the menu to the left).

## Help

The very active [Naomi Community Forum](https://community.projectnaomi.com) provides many more details and hints.
If you run into any problems, use the search function or open a new thread with your detailed question.

<DocPreviousVersions/>
<EditPageLink/>
