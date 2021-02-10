---
title: Installation Overview
source: https://github.com/naomiproject/naomi-docs/blob/dev/installation/index.md
currentVersion: 2.2 
currentMilestoneVersion: 3.0.M16
currentNightlyVersion: Naomi-Nightly
meta:
  - property: og:title
    content: "Installation Overview"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Installation Overview

Naomi is based on the Jasper framework and is fully written in Python.
As such, it only depends on a python installation, which is available for many platforms.
Although this should make it executable on different platforms, such as, **macOS** and **Windows** and different variants of **Linux** it to date has only throughly been tested on Raspberry Pi OS and Debian Buster.

If you are coming from Jasper please be aware of the fact that Naomi is programmed on a new base and introduces new concepts.
Therefore, tutorials and help you may find on the internet for Jasper **WILL** be outdated in respect to Naomi!

## Platform Recommendations

The [Raspberry Pi (RPi)](rasppi.html) is our system recommendation, in large part because of its performance, popularity and cost effectiveness. In particular it offer a quick and relatively painless setup with our [Naobian](naobian.html) version of the Raspberry Pi OS. However Naomi has been shown to work well other platform desktop and laptop options running the Debian OS.

Please check the menu to the left for all available installation options.

## Prerequisites

Due to the way we have structured the setup of Naomi, there are no software prerequisites (Naomi handles all of that for you!). All you need to run Naomi is compatible hardware & OS.  

Hardware prerequisites are a voice input and output device along with an optional Internet connection for some plugins, such as, the weather forecast.

## Setup variants

Before you can start, two decisions have to be made:

1. Naomi is available as a platform independent archive file or through a package:
    - **Manual setup:** Download and extract a platform independent zip archive: [RPI](rasppi.html), [Linux](linux.html).
    - **Packaged setup:** Install though a package repository, built images, or an All-in-One Application: [Naobian](naobian.html), [Virtual Box](virtualbox.html), & [Docker](docker.html).

2. Stable release, Monthly release, or cutting edge:
    - **Stable:** (Current: **{{$page.frontmatter.currentVersion}}**) are thoroughly tested semi-annual official releases of Naomi. Use the stable version for your production environment if you don't need the latest enhancements and prefer a robust system.
    - **Milestone:** (Current: **{{$page.frontmatter.currentMilestoneVersion}}**) are intermediary releases of the next Naomi version, released about once a month, and they include the new recently added features and bug fixes. They are a good compromise between the current stable version and the bleeding-edge and potentially unstable nightly version. Milestones releases are **Highly Recommended** for most users.
    - **Nightly:** At most 1 or 2 days old and include the latest code. Use nightly for testing out very recent changes, but be aware some nightly versions might be unstable. Use in production at your own risk!

## Installation

Please follow the instructions in the installation page matching your platform (see the menu to the left).

## Help

If you run into any problems, use the search function or open a new thread with your detailed question on the [Naomi Community Forum](https://support.projectnaomi.com).

<DocPreviousVersions/>
<EditPageLink/>
