---
title: Naomi Plugin Exchange
source: https://github.com/naomiproject/naomi-docs/blob/dev/plugins/readme.md
meta:
  - property: og:title
    content: "Naomi Plugin Exchange"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Naomi Plugin Exchange

You can easily search for and install 3rd party plugins through the Naomi Plugin Exchange within Naomi itself or by following the instructions located on a specific plugins page located in the [NPE](/plugins/).

You can search for available plugins using the `--list-available-plugins` flag with `Naomi.py`

```terminal
$ ./Naomi.py --list-available-plugins
************************************************************
*                    Naomi Assistant                       *
* Made by the Naomi Community, based on the Jasper Project *
* Source code available from                               *
*    https://github.com/NaomiProject/Naomi                 *
************************************************************
Available Plugins:
Control LED (speechhandler [1.0.1]) - A simple module that combines Naomi and the Arduino platform to show possibilities in IOT and new interactions.
frotz (speechhandler [0.1.0]) - Would you like to play a game?
googlecalendar (speechhandler [1.1.0]) - Set and retrieve events from your Google calendar
Respeaker 4Mic Volume (visualizations [1.0.0]) - LED Display for SeeedStudio Respeaker
You're Welcome (speechhandler [0.0.1]) - Answers "Thank you" with "You're welcome"
```
Available plugins are listed as `Name (category [version]) - Description`

Use the `--install` flag to install a plugin:

```terminal
$ ./Naomi.py --install "You're Welcome"
************************************************************
*                    Naomi Assistant                       *
* Made by the Naomi Community, based on the Jasper Project *
* Source code available from                               *
*    https://github.com/NaomiProject/Naomi                 *
************************************************************
Installing You're Welcome...
Plugin "You're Welcome" is enabled
Plugin "You're Welcome" installed to /home/pi/.config/naomi/plugins/speechhandler/Youre_Welcome
```

Additional flags allow you to disable or re-enable a plugin or remove a plugin completely.

<DocPreviousVersions/>
<EditPageLink/>
