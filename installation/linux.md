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

Naomi has been developed primarily with the RaspberryPi platform in mind running a current version of Debian such as Raspberry PI OS. However some effort has been started to generalize the installer to run on other Linux platform that supports python but it is a work in progress.
## On Debian Buster Installation
To date effort has been focused on getting a solid install presence on a Debian Buster release which should support variants such as Ubuntu, Mint, Raspberry Pi OS, etc. 
There are basically two approaches to getting Naomi up and running in this environment. The software can be downloaded directly from the git repository [here](https://github.com/NaomiProject/Naomi) and then installed by running the sh naomi-setup.py script in a terminal session. Alternately, and likely more straightforward for most, you may use the following "one liner". In a a terminal session enter the following line:
```shell
. <( wget -O - https://installers.projectnaomi.com/naomi-setup.sh )
```
Installing the software by either method will result in you being prompted successively for input to direct the install process:  
1. You will be given the choice to continue with the install, you likely wish to enter "Y"
2. Next will be a prompt for uninterrupted vs a more guided install. Uninterrupted allows the process to proceed with least user interaction.
3. You will be asked which release level of the software you want to install. For new users select "1" for Stable.
4. The software install process will begin and during it you will be prompted for your password to allow sudo to install software. It can take from 30 minutes to 3 hours to complete but typically install times are toward the lower end of the range.
5. When the install finishes and the command prompt returns see the section [Environmental Initialization](./setup/setup) to complete system setup. 

## On Other Linux Installation
As yet the development team has not tested installation on other flavours of Linux. It is expected this can be done without great effort but it is likely there will be some dependencies issues from system to system. If you decide to tackle the challenge we would greatfully appreciate hearing about your experience, particularly if successful in which case we would encourage your additions for the project.

<DocPreviousVersions/>
<EditPageLink/>
