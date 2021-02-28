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
If your speak "Naomi", assuming [Passive Listening](profile.html) is false, followed by any 
of the keywords in bold you should get a response.

- **"Email"** Listen to Mails from your Email account.  
- **"Time"** Tells you the current time.
- **"Hacker"** Check out the latest headlines on Hacker News.
- **"Joke"** Tells you a cheezy "Knock Knock" joke.
- **"Life"** What's the meaning of Life?
- **"Music"** Control your MPD server and listen to music.
- **"News"** Stay informed what's going on with the News plugin.
- **"Shutdown"** Shutdown Naomi.
- **"Stop"** Stops whatever Naomi is doing.
- **"Weather"** WWIS (World Weather Information Service) local weather forcaste where available.

## Next Step

Naomi is a very flexible environment open to exploration of many aspects of speech 
recognition and skills activation. It can be used to examine various approaches to 
the elements of speech processing in the areas of 
[voice activation detection](./configuration/vads.html) (VAD),
[speech-to-text](./configuration/stt.html) (STT), 
[text-to-intent](./configuration/tti.html) (TTI) or 
[text-to-speech](./configuration/tts.html) (TTS). However, it is likely
that the majority of users are interested in developing skill for Naomi to directly 
interact with a user. In this light a tutorial **(Under Development)** on the development of a simple speechhandler 
plugin is provided [here](tutorial.html). This plugin will give Naomi the basic skill to
time short periods.

<DocPreviousVersions/>
<EditPageLink/>
