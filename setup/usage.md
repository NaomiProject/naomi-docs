---
title: Usage
source: https://github.com/naomiproject/naomi-docs/blob/dev/setup/usage.md
meta:
  - property: og:title
    content: "Usage Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Using Naomi

With your audio hardware connected and configured and the profile appropriately populated 
you are ready to run. From the terminal enter the following.
```shell
Naomi
```
If you are presented with the Naomi logo and asked how you can be helped, try asking, 
"Naomi, what is today's weather." or "Naomi what is the time." You should 
hopefully be rewarded for all the hard work you have put in so far. To exit Naomi simply use 
"Naomi, shutdown!"  

## Listing of Naomi Skills
Naomi by default comes with a number of plugin based pre-installed voice assistant type skills. If you speak "Naomi", assuming [Passive Listening](profile.html#passive-listening) is false, followed by any 
of the keywords in bold below you should get a response. You may access the plugin specific write ups to get more detail
on the workings of each by click on the activation word.

- **[Email](plugins/speechhandlers/Check-Email/)** Listen to Mails from your Email account.  
- **[Time](plugins/speechhandlers/Clock/)** Tells you the current time.
- **[Hacker](plugins/speechhandlers/HackerNews/)** Check out the latest headlines on Hacker News.
- **[Joke"]** Tells you a cheezy "Knock Knock" joke.
- **[Life](plugins/speechhandlers/Life/)** What's the meaning of Life?
- **[Music](plugins/speechhandlers/Mdpcontrol/)** Control your MPD server and listen to music.
- **[News](plugins/speechhandlers/News/)** Stay informed what's going on with the News plugin.
- **[Shutdown]** Shutdown Naomi.
- **[Stop]** Stops whatever Naomi is doing.
- **[Weather](plugins/speechhandlers/WWIS-Weather/)** WWIS (World Weather Information Service) local weather forcaste where available.

## Next Step

In many case the new user will be first interested in exploring the development of new voice 
assistant skills to allow Naomi to directly interact with a user. This is done through the creation 
of speechhandler plugins. The details of the structure and process of speechhandler plugins development may be found
[here](../developer/plugins/speechhandler_plugin.html).

Not only can Naomi be used to create a voice assistant but it has also been built to provide a very 
flexible environment open to exploration of many aspects of speech 
recognition and skills activation. It can be used to examine various approaches to 
the elements of speech processing in the areas of 
[voice activation detection](./configuration/vads.html) (VAD),
[speech-to-text](./configuration/stt.html) (STT), 
[text-to-intent](./configuration/tti.html) (TTI) or 
[text-to-speech](./configuration/tts.html) (TTS).
Like speechhandlers plugins may also be created in all these areas to test or extend Naomi's
capability.

Plugins are fundamental to Naomi's use and operation, and to faciitate
their creation and exchange are the Naomi Plugin Editor (NPEE) and Naomi Plugin Exchange (NPEx)
are available. The NPEE is a boiler plate editor which guides the user through the entry
of plugin data and details on its use may be found [here](/developer/plugins/npeeditor.html).
The NPEX on the other hand is the overall environment to support plugin sharing and is
covered [here](/plugins/).

<DocPreviousVersions/>
<EditPageLink/>
