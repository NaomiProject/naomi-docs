---
title: Plugins Development
source: https://github.com/naomiproject/naomi-docs/blob/dev/developer/plugins/index.md
meta:
  - property: og:title
    content: "Plugins Development"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Plugins Development

Naomi's core strength is the plugin system. This means that for almost anything you
would like to change about Naomi, you only need to write a plugin. Plugins allow you
to quickly and easily test a variety of audio engines, speech to text engines,
text to speech engines, text to intent engines, voice activity detection engines, etc.
without having to change anything in the Naomi core.

Plugins work by defining a standard interface that plugins of the class must conform
to. That way they become interchangeable within Naomi.

Current plugin categories and classes include:

| Plugin type      | Category | Parent Class    |
|:----------------:|:--------:|:---------------:|
| [Audio Engine](./audioengine_plugin.html) | audioengine | plugin.AudioEnginePlugin |
| [Speech Handler](./speechhandler_plugin.html) | speechhandler | plugin.SpeechHandlerPlugin |
| [Text to Intent](./tti_plugin.html) | tti | plugin.TTIPlugin |
| [Text to Speech](./tts_plugin.html) | tts | plugin.TTSPlugin |
| [Speech to Text](./stt_plugin.html) | stt | plugin.STTPlugin |
| [Speech to Text Trainer](./stt_trainer_plugin.html) | stt_trainer | plugin.STTTrainerPlugin |
| [Voice Activity Detection](./vad_trainer_plugin.html) | vad | plugin.VADPlugin |
| [Visualizations](./visualizations_plugin.html) | visualizations | plugin.VisualizationsPlugin |

Click on a plugin type above for more detailed development information.

<DocPreviousVersions/>
<EditPageLink/>
