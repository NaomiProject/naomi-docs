---
id: googlestt
label: GoogleCloudSTT
title: GoogleCloudSTT - Speech to Text
type: stts
description: "This is an example readme for testing purposes"
logo: images/plugins/googlestt.png
source:
meta:
  - property: og:title
    content: "GoogleCloudSTT - Speech to Text"
  - property: og:description
    content: "This is an example readme for testing purposes"
---

# GoogleCloudSTT - Speech to Text

<PluginLogo/>

You will need a token that you receive for free by registering an account on the Google Cloud website

[Follow steps here](https://cloud.google.com/speech-to-text/)

In particular, this page explains how to register and how to retrieve your private key:

[Google STT quick start](https://cloud.google.com/speech-to-text/docs/quickstart-protocol)

After enabling the google speech API as described above, download the API key as a json file and set the "google: credentials_json:" 
key in profile.yml to the location of this file.

>Note: Do not forget to enable billing! Even if you use the free account, you still have to enable it in order for the engine to work!



<EditPageLink/>
