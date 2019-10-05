---
title: DeepSpeech Setup
source: https://github.com/naomiproject/naomi-docs/blob/dev/plugins/deepspeech-setup.md
meta:
  - property: og:title
    content: "DeepSpeech Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# DeepSpeech setup

DeepSpeech now provides precompiled packages via pip, so you won't have to build it yourself anymore.

To install DeepSpeech go ahead and install it with pip:
```shell
[~]$ sudo pip3 install deepspeech
```

Note: DeepSpeech did not run very well on the Raspberry Pi because the language model was too large to fit in memory, and without it DeepSpeech just returns raw phonemes.

Now you need to download the language models for your DeepSpeech version:
  - Check the version here: https://pypi.org/project/deepspeech/ (current one is v0.5.1)
  - Copy this and replace the version number with your version:
  ```shell
    [~]$ wget https://github.com/mozilla/DeepSpeech/releases/download/v0.5.1/deepspeech-0.5.1-models.tar.gz
  ```
  - And extract the downloaded file:
  ```shell
    [~]$ tar xvfz deepspeech-0.5.1-models.tar.gz
  ```
Great! You just downloaded the pre-trained model from the DeepSpeech project. You should make sure to look at the Common Voice project
 (https://voice.mozilla.org/en) and consider contributing in order to help with higher quality models in the future.

The last step is to add DeepSpeech to your profile like this:

  I recommend using PocketSphinx for passive listening and DeepSpeech for active listening. To use it as the active listener with Naomi, you will need to add a section like this to your profile.yml file:

```yaml
active_stt:
  engine: deepspeech-stt
deepspeech:
  model: '/home/user/models/output_graph.pb'
  alphabet: '/home/user/models/alphabet.txt'
  language_model: '/home/user/models/lm.binary'
  trie: '/home/user/models/trie'
```

<DocPreviousVersions/>
<EditPageLink/>
