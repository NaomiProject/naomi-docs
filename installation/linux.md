---
title: Linux
source: https://github.com/naomiproject/naomi-docs/blob/dev/installation/linux.md
meta:
  - property: og:title
    content: "Linux Guild"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Naomi on Linux

Naomi has been developed primarily with the RaspberryPi platform in mind running a current version of the Raspberry PI OS. However some effort has been started to generalize it to run on other Linux platform that supports python but it is a work in progress.
## Debian Buster Installation
To date effort has been focused on getting a solid install presence on a Debian Buster release.  
There are basically two approaches to getting Naomi up and running in this environment. The software can be downloaded directly from the git repository [here](https://github.com/NaomiProject/Naomi) and then installed by running the sh naomi-setup.py script in a terminal session. Alternately, and likely more straightforward for most, you may use the following "one liner". In a a terminal session enter the folling line:
```shell
. <( wget -O - https://installers.projectnaomi.com/naomi-setup.sh )
```
Installing the software by either method will result in you being prompted successively for input to direct the install process:  
1. Uninterrupted or guided install
2. Release level of software to install
3.  
On completion of the install you should 

## Other Linux Installation
As yet the development team has not tested installation on other flavours of Linux. It is expected this can be done without great effort but it is likely there will be some dependencies issues from system to system. If you decide to tackle the challenge we would greatfully appreciate hearing about your experience, particularly if successful in which case we would encourage your additions for the documentation.

<DocPreviousVersions/>
<EditPageLink/>
