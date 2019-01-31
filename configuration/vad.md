---
title: VAD
source: https://github.com/naomiproject/naomi-docs/blob/master/configuration/vad.md
meta:
  - property: og:title
    content: "VAD Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# VAD Configuration

VAD stands for Voice Activity Detection and is software that alerts Naomi that you are speaking

| Engine name   | Privacy Respect | Type    | Self Hosting | Requests (free account) | Quality     | Platform        |
|:-------------:|:---------------:|:-------:|:------------:|:-----------------------:|:-----------:|:---------------:|
| [*SNR_Vad*](#snr-vad)    | 👍              | Offline  | Yes           | Unlimited                  | Good     | Any             |
| [*WebRTCVAD*](#webrtc-vad) | 👍              | Offline  | Yes           | Unlimited              | Really Good  | Any             |

You will need to pick one of the above and then follow the instructions below that is denoted for the STT engine you select

## SNR_Vad

This is based on the original Voice Activity Detection for Naomi, which basically sets a threshold level and considers
anything above the threshold speech to be processed, and anything below that threshold background noise to be ignored.

I used to have issues with setting the threshold to the right level, so in this version I collect volume levels and
consider anything above the mean plus 1.5 * standard deviation to be audio to be processed.

I also reset the counts every 100 samples to keep the formula adjusting to changes in background noise levels.

This is the default plugin for Voice Activity Detection because it is implemented in pure Python and does not have
any external requirements.

To use it does not require you to add anything to your profile.yml file, but if you explicitely want to set it, or if
you want to set any of the options connected to it, you can add a section like:
```
vad_engine: snr_vad
snr_vad:
  timeout: 1
  minimum_capture: 0.25
  threshold: 20
```
* timeout: how long it has to go without hearing anything before deciding you are finished speaking (in seconds)
* minimum_capture: the minimum length of a piece of captured audio that will be returned for processing (in seconds)
* threshold: the initial volume level in decibels over which the engine will interpret as talking.

All the options are optional and have sane defaults.


## WebRTC_VAD

This uses the WebRTC Voice Activity Detection module developed at Google for the [WebRTC](https://webrtc.org/) project.
To use this, you will need to install the [webrtcvad](https://github.com/wiseman/py-webrtcvad) python module which is
available through PyPi
```console
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

<DocPreviousVersions/>
<EditPageLink/>
