---
title: Profile
source: https://github.com/naomiproject/naomi-docs/blob/dev/setup/profile.md
meta:
  - property: og:title
    content: "Profile Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Profile Setup

The Naomi profile is a relatively small hierarchical database in YAML format. It is located in 
the Naomi configuration directory which defaults to **~/.config/naomi** (a hidden directory), 
but can be overridden by setting the NAOMI_SUB environment variable. The default 
location for the profile.yml file is **~/.config/naomi/configs/profile.yml**.

If Naomi cannot locate the profile.yml file, it will walk you through the settings 
required to set up the core program and plugins. You can also re-configure the Naomi profile by 
running:
```shell
./Naomi --repopulate
```
This will walk you through some plugin-specific settings which are described in more detail in 
the specific plugin sections (
[TTI](../configuration/tti.html),
[TTS](../configuration/tts.html), 
[STT](../configuration/stt.html), 
[VAD](../configuration/vad.html)) but there are also a few setting that are specific to both the core 
Naomi program and its operation that it will help setup.

# Running the Repopulate Process

As the process runs the user will be prompted to either answer a simple **y**es or **n**o question 
or to enter a value before proceeding. If there is a default value it will be highlighted just 
before the input area. Hitting enter will select the default or blank if there is none specified.
There is also a fair bit of annotation to assist with decidiing the option to select.

The following lists the main profile items you will be prompted for and provides minor guidance and 
explanation where appropriate:

- **Select Language** This informs Naomi which language model to use. In the current implementation
EN is the most supported language.
- **Audiolog level** Audio logging allows you to store recordings of yourself which may be later used
to help train the system.
- **Heard you response** Naomi's way to let you know, "I've heard you!"
- **Configuring Naomi** What name would you like to call the system. Default "Naomi".
- **Audio engine** Typically best to go with default unless you are aware of a reason otherwise. 
You can always come back and change.
- **Audio output device** Typically best to go with default.
- **Beep test** If you do not hear the beep troubleshoot audio as required. See previous section.
- **Audio input device** Typically best to go with default.
- **Audio input device test** Respond as appropriate.
- **Passive speech to text engine** Typically best to go with default.
- **Active speech to text engine** Typically best to go with default.
- **Special speech to text engine** Typically best to go with default.
- **Text to speech engine** Typically best to go with default.
- **Passive listening** For detail see section on [passive listening](#passive-listening) below. 
This can be set to True (y) or False (n). Typically best to go with default.
- **Print transcript** Typically best to go with default. More detail [here](#print-transcript)
- **Email address** If you enter an email address you will need the IMAP details of your 
mail server in order to complete subsequent items. Press Enter to bypass.
- **Phone number** 
- **Carrier** Phone provider.
- **WWIS country** Select country you wish the weather for from the list.
- **WWIS region** Region, province or state from the list.
- **WWIS city** Closest city from the list.
- **Temperature scale** Default Fahrenheit but the world uses Celsius
- **MPDcontrol server** Typically best to go with default. Setup of MPD server is beyond scope of Naomi.
- **MPDcontrol port** Typically best to go with default.
- **While music is playing** Typically best to go with default.
- **Timezone**
- **PocketSphinx hmm file** Typically best to go with default.
- **PocketSphinx FST file** Typically best to go with default.
- **Phonetisaurus executable** Typically best to go with default.

## Print Transcript
This setting is used to tell Naomi to display a transcript of conversations. It is especially 
useful for troubleshooting problems with the passive and active speech to text engines. Both 
the passive and active passes will be printed with a "<" indicating the passive engine transcribe 
result and "<<" indicating the active engine transcribe result. ">>" indicates something naomi 
is speaking using the Text To Speech engine.

## Passive Listening

When the value is False, 
the default, Naomi will poll the incoming audio using the passive_stt engine listening 
for the (Naomi) keyword. When the keyword is detected, Naomi will either play a high beep 
noise or say something to let you know it is listening. At that point it will start 
recording audio. When it detects that the user has stopped speaking, it will stop 
recording and analyze the captured audio using the active_stt engine. This makes Naomi 
work similar to the way that Siri works.

When the value is True, Naomi will start recording when you start speaking, then 
when it detects a pause in the audio it will use the passive_stt engine to check 
for the keyword, and if the keyword is found, will pass the same block of recorded 
audio directly to the active_stt engine for analysis.


<DocPreviousVersions/>
<EditPageLink/>
