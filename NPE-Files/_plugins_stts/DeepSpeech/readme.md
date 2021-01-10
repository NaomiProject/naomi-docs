---
id: deepspeech
label: DeepSpeech
title: DeepSpeech - Speech to Text
type: stts
description: "This is an example readme for testing purposes"
logo: images/plugins/deepspeech.jpg
source: https://github.com/NaomiProject/naomi-docs/edit/dev/NPE-Files/_plugins_stts/DeepSpeech/readme.md
meta:
  - property: og:title
    content: "DeepSpeech - Speech to Text"
  - property: og:description
    content: "This is an example readme for testing purposes"
---

# DeepSpeech - Speech to Text

<PluginLogo/>

DeepSpeech now provides precompiled packages via pip, so you won't have to build it yourself anymore.

To install DeepSpeech go ahead and install it with pip:
```shell
[~]$ sudo pip3 install deepspeech
```

Mozilla Deepspeech uses the KenLM language model generator to build language models based on the templates
in your installed speechhandler plugins. Mozilla Deepspeech is now included in python-requirements.txt so
will be installed automatically when you install Naomi.

The first time you activate the Deepspeech plugin, it will perform the following steps:

Download the DeepSpeech source code that matches the deepspeech python module you have installed. It doesn't
have to compile it, but we need some support programs that come with the source code for building language
models.

Download the acoustic model, which I assume is primarily trained on midwestern english pronunciations. Tools
for training or adapting the acoustic model to your own voice will be coming sometime in 2021.

Please take a look at the Common Voice project (https://voice.mozilla.org/en) and consider contributing
recordings in order to help with higher quality models in the future.

The last step is to add DeepSpeech to your profile like this:

```yaml
active_stt:
  engine: deepspeech-stt
deepspeech:
  model: '/home/user/models/output_graph.pb'
  alphabet: '/home/user/models/alphabet.txt'
  language_model: '/home/user/models/lm.binary'
  trie: '/home/user/models/trie'
```

<EditPageLink/>
