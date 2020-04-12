---
id: webrtcvad
label: WebRTCVAD
title: WebRTCVAD - Voice Activity Detection
type: vads
description: "WebRTC Voice Activity Detection module developed at Google for Naomi"
source:
meta:
  - property: og:title
    content: "WebRTCVAD - Voice Activity Detection"
  - property: og:description
    content: "WebRTC Voice Activity Detection module developed at Google for Naomi"
---

# WebRTCVAD - Voice Activity Detection


This uses the WebRTC Voice Activity Detection module developed at Google for the [WebRTC](https://webrtc.org/) project.
To use this, you will need to install the [webrtcvad](https://github.com/wiseman/py-webrtcvad) python module which is
available through PyPi
```shell
$ pip install webrtcvad
```

To use this engine for voice activity detection, add the following to your profile.yml:
```
vad_engine: webrtc_vad
webrtc_vad:
  timeout: 1
  minimum_capture: 0.25
  aggressiveness: 1
```
* timeout: how long it has to go without hearing anything before deciding you are finished speaking (in seconds)
* minimum_capture: the minimum length of a piece of captured audio that will be returned for processing (in seconds)
* aggressiveness: how aggressively to filter out non-speech. 0 is the least aggressive and 3 is the most aggressive.

The options under webrtc_vad are all optional and set to sane defaults, so all you really need is the "vad_engine: webrtc_vad" line.


<EditPageLink/>
