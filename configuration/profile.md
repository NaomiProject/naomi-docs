---
title: Profile
source: https://github.com/naomiproject/naomi-docs/blob/master/configuration/profile.md
meta:
  - property: og:title
    content: "Profile Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Profile Setup

The Naomi profile is a small hierarchical database in YAML format. It is located in the Naomi configuration directory which defaults to ~/.config/naomi (a hidden directory), but can be overridden by setting the NAOMI_SUB environment variable. The default location for the profile.yml file is `~/.config/naomi/configs/profile.yml`.

If Naomi cannot locate the profile.yml file, it will walk you through the settings required to set up the core program and plugins. You can also re-configure Naomi by passing in the --repopulate flag, ie: `$ ./Naomi.py --repopulate`

Some plugin-specific settings are described in the specific plugin sections ([Audio](audio.html), [TTS](tts.html), [STT](stt.html), [VAD](vad.html)) but there are also a few setting that are specific to the core Naomi program and not addressed in the `populate.py` program that you might want to be aware of.

**passive_listen** (default: False) - this is a boolean value and can be set to True or False. 
When the value is False, the default, Naomi will poll the incoming audio using the passive_stt engine listening for the keyword. When the keyword is detected, Naomi will either play a high beep noise or say something to let you know it is listening. At that point it will start recording audio. When it detects that the user has stopped speaking, it will stop recording and analyze the captured audio using the active_stt engine. This makes Naomi work similar to the way that Siri works with conversations proceeding along the lines of:
```
You: Naomi
Naomi: high beep
You: What time is it?
Naomi: low beep
Naomi: It is 4:30 PM right now
```
When the value is True, Naomi will start recording when you start speaking, then when it detects a pause in the audio it will use the passive_stt engine to check for the keyword, and if the keyword is found, will pass the same block of recorded audio directly to the active_stt engine for analysis, resulting in conversations that proceed more like this:
```
You: Naomi, what time is it?
Naomi: high beep
Naomi: It is 4:30 PM right now
Naomi: low beep
```
> Example:
```shell
passive_listen: True
```

**passive_stt: engine:** (default: same as active_stt: engine:)- this setting is used to configure the passive speech to text engine, allowing you to specify different engines for passive and active listening. It has one sub-setting which is "engine". This is the engine that will listen for you to say the wake word, and then either activate active listening mode or pass the audio to the active listening engine depending on the value of the passive_listen setting.

> Example:
```shell
passive_stt:
  engine: sphinx
```

**print_transcript**: (default: False) - this setting is used to tell Naomi to print out a transcript of conversations. It is especially useful for troubleshooting problems with the passive and active speech to text engines. Both the passive and active passes will be printed with a "<" indicating the passive engine transcribe result and "<<" indicating the active engine transcribe result. ">>" indicates something naomi is speaking using the Text To Speech engine. A query about the time while passive_listening is enabled and using the pocketsphinx engine for both active and passive listening might look something like this:
```
<  ['NAOMI ON']
<< ['NO MEANING TIME']
>> It is 4:30 PM right now
```
In this case, the passive engine was able to understand 'Naomi' and the active engine was able to understand 'time'. The passive engine did not know the word 'time' so it selected the best match it could find in its dictionary, and the active engine did not know the word 'Naomi' so it also tried to find the nearest match.

> Example:
```shell
print_transcript: True
```

<DocPreviousVersions/>
<EditPageLink/>