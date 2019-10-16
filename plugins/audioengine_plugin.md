---
title: Audio Engine Plugins Development
source: https://github.com/naomiproject/naomi-docs/blob/dev/plugins/audioengine_plugin.md
meta:
  - property: og:title
    content: "Audio Engine Plugins Development"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Audio Engine Plugin Development

Parent Class: plugin.AudioEnginePlugin
Required Methods:
&nbsp;&nbsp;**get_devices(device_type=audioengine.DEVICE_TYPE_ALL)**
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The device_type parameter can be passed one of the following values:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;naomi.audioengine.DEVICE_TYPE_INPUT
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;naomi.audioengine.DEVICE_TYPE_OUTPUT
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;naomi.audioengine.DEVICE_TYPE_ALL
&nbsp;&nbsp;&nbsp;&nbsp;Returns list of AudioDevice objects

&nbsp;&nbsp;**get_default_device(output=True)**
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;output can be either True (return output device) or False
&nbsp;&nbsp;&nbsp;&nbsp;Returns an AudioDevice object

&nbsp;&nbsp;**get_device_by_slug(slug)**
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;slug is a string that describes an audio device
&nbsp;&nbsp;&nbsp;&nbsp;Returns an AudioDevice object

Each AudioEngine has to define its own AudioDevice object as well.

<DocPreviousVersions/>
<EditPageLink/>
