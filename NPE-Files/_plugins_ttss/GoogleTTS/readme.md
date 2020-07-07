---
id: googletts
label: GoogleTTS
title: GoogleTTS - Text to Speech
type: ttss
description: "high performance, multi-channel, text-to-speech (TTS) server"
logo: images/plugins/googletts.png
source: https://github.com/NaomiProject/naomi-docs/edit/dev/NPE-Files/_plugins_ttss/GoogleTTS/readme.md
meta:
  - property: og:title
    content: "GoogleTTS - Text to Speech"
  - property: og:description
    content: "high performance, multi-channel, text-to-speech (TTS) server"
---

# GoogleTTS - Text to Speech

<PluginLogo/>

You will need a token that you receive for free by registering an account on the Google Cloud website

[Follow steps here](https://cloud.google.com/text-to-speech/)

In particular, this page explains how to register and how to retrieve your private key:

[Google TTS quick start](https://cloud.google.com/text-to-speech/docs/quickstart-protocol)

After enabling the google speech API as described above, download the API key as a json file and set the "google: credentials_json:" 
key in profile.yml to the location of this file.

>Note: Do not forget to enable billing! Even if you use the free account, you still have to enable it in order for the engine to work!


<EditPageLink/>
