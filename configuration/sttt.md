---
title: NaomiSTTTrainer
source: https://github.com/naomiproject/naomi-docs/blob/master/configuration/sttt.md
meta:
  - property: og:title
    content: "NaomiSTTTrainer"
  - property: og:description
    content: Overview of using NaomiSTTTrainer.py to improve word recognition rates
---

# NaomiSTTTrainer.py

NaomiSTTTrainer.py is an executable program that runs in the root of Naomi.
It can be used to train Naomi to better recognize your voice by using samples
that Naomi has collected.

To get started, either run Naomi with the --save-audio flag, or add the
following lines to your profile.yml file (~/.config/naomi/configs/profile.yml):

```
audiolog:
    save_audio: True
```

Run Naomi for a bit and collect a couple of dozen recordings of yourself talking
with Naomi. Then return to the Naomi install directory and run:

```
$ ./NaomiSTTTrainer.py
```

If you are running Naomi on a full desktop, your default browser will open a
new window allowing you to access the recordings. Otherwise, a url will be
displayed that you can use to access the recordings from another computer.

Open the URL (if it was not automatically opened for you) and you will see
something similar to this:

```
|==============================================|
|Verify transcriptions|Train STT Engines       |
|==============================================|
|Naomi transcription 1 of 24 (passive)         |
|> o===== 0:00/0:03 < ====o                    |
|Naomi heard "NAOMI WHAT TIME IS IT"           |
|What did you hear?                            |
|[ ] The transcription was correct. I heard the|
|    same thing                                |
|[ ] The transcription was not correct. This is|
|    what I heard:                             |
|    [                     ]                   |
|[ ] This was just a noise with no voices      |
|[ ] This was not directed to Magic Voice or   |
|    was too unclear to understand             |
|Speaker:                                      |
|[              ]                              |
|                                              |
|Intent: ClockIntent (0.73)                    |
|Correct intent: [ClockIntent]                 |
|                                              |
|[Submit]                                      |
|[Prev][Next]                                  |
================================================
```

Use the audio player to listen to the clip, then select the correct radio response.
Mark "The transcription was correct" if you agree with what Naomi heard.
Mark "The transcription was not correct" and enter the correct transcription if Naomi did not hear you correctly.
The "just a noise with no voices" option can be used to improve the Voice Activity Detection.
The final option is currently used to mark the recording as trash that should not be used for training.
You should use this option if you can't be sure what was said, or if the conversation is not directed
to Naomi, or if multiple people are talking in the same recording.

Use the "Speaker" textbox to enter the name of the speaker if known. Currently this is not used for
anything, but eventually we plan to train Naomi to recognize an individual speaker by voice, and also to choose
a speech recognition model based on who is speaking.

Intent shows the intent that Naomi identified as being what the user wanted along with the confidence.
If Naomi did not get the intent correct, then use the drop down list to select the correct intent.
If Naomi should not have associated the request with any intent, select "unclear".

Verify or correct all of the transcriptions you have. You will hopefully have a couple of "false positives" where
Naomi started recording after a noise that was not a voice, and a couple of recordings of someone speaking the
wake word. When you are finished, click on the "Train STT Engines" tab at the top of the page.

You will a page like:

```
|==============================================|
|Verify transcriptions|Train STT Engines       |
|==============================================|
|[Adapt Pocketsphinx]                          |
|                                              |
================================================
```

Right now, the only STT Trainer plugin available is the "Adapt Pocketsphinx". This module allows you to
adapt the standard pocketsphinx model for your language to your voice. Research into training speech
recognition engines is ongoing and eventually other plugins will be available.

Press the "Adapt Pocketsphinx" button and Naomi will start adapting the model. Eventually you should see
a "Training Complete" message at the bottom of the page. From this point forward, you should notice a
marked improvement in Naomi's ability to understand you.

We don't provide word error rate information through the interface, but if you are interested you can
get them directly from the database.

```
$ cd ~/.config/naomi/audiolog
$ sqlite3 audiolog.db
sqlite> select avg(wer) from audiolog where datetime<(select datetime from trainings where rowid=1) and verified_transcription!='';
.42
sqlite> select avg(wer) from audiolog where datetime>(select datetime from trainings where rowid=1) and verified_transcription!='';
.25
```

After collecting the first set of audiolog files, it's a good idea to only capture active listening.
This will prevent Naomi from recording as many random sounds around the house, and only record what
is said after hearing the wake word, which will make verifying additional transcriptions much more
productive. Change your profile.yml file to:

```
audiolog:
  save_active_audio: true
```

<EditPageLink/>