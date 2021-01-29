---
title: Audio Engine Plugins
source: https://github.com/naomiproject/naomi-docs/blob/dev/developer/plugins/audioengine_plugin.md
meta:
  - property: og:title
    content: "Audio Engine Plugins Development"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Audio Engine Plugin Development

Parent Class: plugin.AudioEnginePlugin<br />
Required Methods:<br />
&nbsp;&nbsp;**get_devices(device_type=audioengine.DEVICE_TYPE_ALL)**<br />
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The device_type parameter can be passed one of the following values:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;naomi.audioengine.DEVICE_TYPE_INPUT<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;naomi.audioengine.DEVICE_TYPE_OUTPUT<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;naomi.audioengine.DEVICE_TYPE_ALL<br />
&nbsp;&nbsp;&nbsp;&nbsp;Returns list of AudioDevice objects<br />

&nbsp;&nbsp;**get_default_device(output=True)**<br />
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;output can be either True (return output device) or False<br />
&nbsp;&nbsp;&nbsp;&nbsp;Returns an AudioDevice object<br />

&nbsp;&nbsp;**get_device_by_slug(slug)**<br />
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;slug is a string that describes an audio device<br />
&nbsp;&nbsp;&nbsp;&nbsp;Returns an AudioDevice object<br />

Each AudioEngine has to define its own AudioDevice object as well.

<DocPreviousVersions/>
<EditPageLink/>
