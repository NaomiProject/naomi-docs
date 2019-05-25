---
title: STT
source: https://github.com/naomiproject/naomi-docs/blob/dev/configuration/stt.md
meta:
  - property: og:title
    content: "STT Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# STT Configuration

STT, stands for Speech to Text, and is software that transforms spoken words & sentences into text, which is how Naomi can understand you

| Engine name      | Privacy Respect | Type    | Self Hosting | Requests (free account) | Quality     | Platform |
|:----------------:|:---------------:|:-------:|:------------:|:-----------------------:|:-----------:|:--------:|
| [*Wit.ai*](#witai) | 👎              | Online  | NO           | Unlimited               | Really good | Any      |
| [*Google Cloud STT*](#google-cloud-stt) | 👎              | Online  | NO           | ?                       | Really good | Any      |
| [*AT&T Speech API*](#att-stt)  | 👎              | Online  | NO           | ?                       | ?           | Any      |
| [*Pocketsphinx*](#pocketsphinx)     | 👍              | Offline | YES          | Unlimited               | ?           | Linux 🐧 |
| [*Mozilla DeepSpeech*](#mozilla-deepspeech)       | 👍              | Offline | YES          | ?                       | ?           | Linux 🐧 |
| [*Julius*](#julius)           | 👍              | Offline | YES          | Unlimited               | ?           | Linux 🐧 |
| [*Kaldi*](#kaldi-server)            | 👍              | Online  | YES          | Unlimited               | ?           | Linux 🐧 |

You will need to pick one of the above and then follow the instructions below that is denoted for the STT engine you select

>Note: For accuracy, really good understanding and easy to use, online solutions are better! But for privacy reasons and to use Naomi without internet access, we recommend the use of offline solutions

## Wit.ai

You will need a token that you receive for free by registering an account on the Wit.ai website

[Follow steps here](https://wit.ai/)

## Google Cloud STT

You will need a token that you receive for free by registering an account on the Google Cloud website

[Follow steps here](https://cloud.google.com/speech-to-text/)

In particular, this page explains how to register and how to retrieve your private key:

[Google STT quick start](https://cloud.google.com/speech-to-text/docs/quickstart-protocol)

After enabling the google speech API as described above, download the API key as a json file and set the "google: credentials_json:" 
key in profile.yml to the location of this file.

>Note: Do not forget to enable billing! Even if you use the free account, you still have to enable it in order for the engine to work!

## AT&T STT

You will need a token that you receive for free by registering an account on the AT&T developer program website

[Follow steps here](https://developer.att.com/blog/at-amp-t-text-to-speech-and-speech-to-text-api-tutorial)

## Pocketsphinx

Install with the following instructions

[Follow steps here](../plugins/pocketsphinx-install.html)

## DeepSpeech

Install with the following instructions

[Follow steps here](../plugins/deepspeech-setup.html)

## Julius

>Note: You will need to train your own acoustic model, which is a very complex task that we do not provide support for!

Install with the following instructions

[Follow steps here](https://julius.osdn.jp/juliusbook/en/desc_install.html)

## Kaldi Server

Install with the following instructions

[Follow steps here](http://kaldi-asr.org/doc/)

<DocPreviousVersions/>
<EditPageLink/>
