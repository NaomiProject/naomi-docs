---
id: frotz
label: Frotz
title: Frotz - Speechhandler
type: speechhandlers
description: "Would you like to play a game?"
logo: images/plugins/frotz.png
source: https://github.com/aaronchantrill/NaomiFrotz/edit/master/README.md
meta:
  - property: og:title
    content: "Frotz - Speechhandler"
  - property: og:description
    content: "Would you like to play a game?"
---


# Frotz - Speechhandler

<PluginLogo/>

This plugin is for playing infocom games with Jasper.

I have included a modified copy of textPlayer from Daniel Ricks (https://github.com/danielricks/textplayer) which does some handy
things like split the location and description into different properties. I've only really worked on Zork1 so far, other games will
probably require some tweaking.

TextPlayer uses a copy of dfrotz. I have included dfrotz.x86_64, dfrotz.i686 and dfrotz.arm7l which were built on Debian Buster, 
Raspbian Stretch x86 and Raspbian Stretch Arm running on a Raspberry Pi 3B+. If you are running on a different system, you will 
probably have to build this. Luckily this is easy and most of the issues have to do with missing shared library files. I found
that I needed to install the following on Ubuntu 16.04:

    ~$ sudo apt install libao-dev libsndfile1 libflac-dev libogg-dev libsndfile1-dev libvorbis-dev pkg-config libmodplug-dev libsamplerate1-dev

You can download dfrotz from github:

    ~$ git clone https://github.com/DavidGriffith/frotz.git
    ~$ cd frotz

Then just build with a target of dfrotz. No need to install it, just drop it into the same directory with textPlayer.

    ~/frotz$ make dfrotz
    ~/frotz$ cp -iv dfrotz ~/.naomi/plugins/speechhandlers/frotz/

To use this with the Pocketsphinx speech to text engine requires some additional work. First, you will need to extract the games 
commands into a corpus file in the games directory with the same root name as your game file. Look at zork1.corpus for an example.
I used Zorkword by Mike Threepoint which can be downloaded from http://mirror.ifarchive.org/if-archive/infocom/tools/zorkword.zip.
Then, since most z-machine games only looked at the first few letters of each word, you may have to guess what some of the words
actually are.

<EditPageLink/>