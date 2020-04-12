---
id: respeakermicvisualization
label: RespeakerMic
title: RespeakerMicVisualization - Visualization
type: visualizations
description: "LED Display for SeeedStudio Respeaker"
source: https://github.com/aaronchantrill/respeaker_4mic_volume/edit/master/README.md
logo: images/plugins/seeed.png
meta:
  - property: og:title
    content: "RespeakerMicVisualization - Visualization"
  - property: og:description
    content: "LED Display for SeeedStudio Respeaker"
---

# RespeakerMicVisualization - Visualization

<PluginLogo/>

This plugin uses the 12 multicolor LEDs on the SeeedStudio Respeaker 4 to
provide visualizations.

Currently, the only visualization is the mic in audio level. This includes
one LED that turns red when Naomi is recording, otherwise it stays green,
and one LED that indicates the threshold above which Naomi starts listening.
This is currently only compatible with the SNR_VAD (Signal to Noise Ratio
Voice Activity Detector) plugin, which is the default for Naomi.

I hope to add additional visualizations eventually. Anyone is welcome to
contribute to this project, just send me a pull request.

## To use this plugin with Naomi:

Install Naomi (https://projectnaomi.com)
```
$ git clone -b naomi-dev https://github.com/NaomiProject/Naomi.git
$ cd Naomi
```

Install the Respeaker Visualizations plugin
`Naomi $ ./Naomi.py --install "Respeaker Visualizations"`

Run Naomi
`Naomi $ ./Naomi.py`

## Adding visualizations

Adding visualizations to Naomi is a little different from adding other
plugins. Instead of selecting a particular visualization plugin, all enabled
visualization plugins are loaded at the same time. This means that you can
have multiple visualizations running at the same time, and each visualization
can have its own take on any emotional cue.

In this case, I have defined a "mic_volume" visualization. This takes 6
parameters: recording, snr, minsnr, maxsnr, mean and threshold.

It is quite possible to have a name collision with someone else writing a
visualization of the same name, so it is important to use **kwargs for
passing parameters. If any of the parameters are missing, then assume
that the request was for something else. So the visualization you are writing
is both for a particular visual device (terminal, respeaker, led array, etc)
and for a particular communication. So instead of naming a visualization
just "respeaker" name it "respeaker_mic_volume" etc.

When calling the visualization, start by importing the visualizations module
from naomi, then use the visualizations.run_visualization() method to actually
call the visualization. This method accepts the name of the method to run,
then it searches through all the visualization plugins that have been loaded
to see if they contain the method being called. All parameters should be
passed in by name so they can be compared to what the visualization is
expecting. This should help prevent collisions. That way, when someone writes
a new visualization in the future that is called by your plugin, it will just
start working without any additional work on your part.


<EditPageLink/>
