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
| [*Wit.ai*](/plugins/stts/Witai/) | 👎              | Online  | NO           | Unlimited               | Really good | Any      |
| [*Google Cloud STT*](/plugins/stts/GoogleCloud/) | 👎              | Online  | NO           | ?                       | Really good | Any      |
| [*AT&T Speech API*](/plugins/stts/ATTSpeech/)  | 👎              | Online  | NO           | ?                       | ?           | Any      |
| [*Pocketsphinx*](/plugins/stts/Pocketsphinx/)     | 👍              | Offline | YES          | Unlimited               | ?           | Linux 🐧 |
| [*Mozilla DeepSpeech*](/plugins/stts/DeepSpeech/)       | 👍              | Offline | YES          | ?                       | ?           | Linux 🐧 |
| [*Julius*](/plugins/stts/Julius/)           | 👍              | Offline | YES          | Unlimited               | ?           | Linux 🐧 |
| [*Kaldi*](/plugins/stts/Kaldi/)            | 👍              | Online  | YES          | Unlimited               | ?           | Linux 🐧 |

You will need to pick one of the above and then follow the instructions below that is denoted for the STT engine you select

>Note: For accuracy, really good understanding and easy to use, online solutions are better! But for privacy reasons and to use Naomi without internet access, we recommend the use of offline solutions

<DocPreviousVersions/>
<EditPageLink/>
