---
id: snrvad
label: SNRVad
title: SNRVad - Voice Activity Detection
type: vads
description: "sets a threshold level and considers anything above the threshold speech to be processed, and anything below that threshold background noise to be ignored"
logo:
source:
meta:
  - property: og:title
    content: "SNRVad - Voice Activity Detection"
  - property: og:description
    content: "sets a threshold level and considers anything above the threshold speech to be processed, and anything below that threshold background noise to be ignored"
---

# SNRVad - Voice Activity Detection

<PluginLogo/>

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

When using SNR_Vad, you will see a volume feedback printout at the bottom of your screen. It looks like this:
```
+||============m=====t==-----||
```
The plus at the front indicates that Naomi is recording for analysis. The m shows the mean average volume level
(using the mean allows Naomi to automatically adjust to a noisy room) and t indicates the threshold, over which
Naomi will pay attention.


<EditPageLink/>
