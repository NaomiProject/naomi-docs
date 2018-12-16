---
title: MaryTTS Server
source: https://github.com/naomiproject/naomi-docs/blob/master/plugins/marytts.md
meta:
  - property: og:title
    content: "MaryTTS Server Guide"
  - property: og:description
    content: an open source platform for developing always-on, voice-controlled applications
---

{% include base.html %}

# This is how to make a marytts server for your own use

## Public tts server config is 4 procs @2.13ghz Xeon with 8GB of RAM

It is currently only using about 3GB with all languages loaded.

I am guessing you can get away with 2gb if your only loading a couple of the voice types.

1. Installed and updated ubuntu 16.04 server.
2. Add webupd8t repo for easy Java install. `sudo add-apt-repository ppa:webupd8team/java -Y`
3. Update apt list. `apt update`
4. Insall Java8,unzip,(build-essential,and git) <-Optional. `apt install oracle-java8-installer unzip build-essential git -Y`
5. Drop root `exit`
6. Get Marytts installer `wget http://mary.dfki.de/download/5.1.2/marytts-installer-5.1.2.zip`
7. Extract it `unzip marytts-installer-5.1.2.zip`

## Now you should have a folder called marytts that you can cd into

1. Change folders with: `cd marytts-installer-5.1.2`
2. Then give it the intial test run with: `./marytts`

## Now you should be able to test the system

Open a web browser and go to `http://<ip_of_tts_server>:59125`

## Next install your language of choice

At the bottom of this page shows a list of all the languages and voices.

To install all of the voices type the following `~/marytts-installer-5.1.2/marytts install`

Or to install a single voice type the following `~/marytts-installer-5.1.2/marytts install:cmu-slt`

Replacing the letters after `:` with your choice.

## -well close to- Oneliner  to do a **Full LOAD LANGUAGE SUPPORT**

Check with wiki and marytts for complete list of language support.

Make sure you are root with the # on the terminal. The script expects to drop sudo, to download and install the tts server.

Otherwise use `sudo su`

Then this:

```console
add-apt-repository -y ppa:webupd8team/java && apt update && apt install -y oracle-java8-installer unzip build-essential git && exit
```

```console
wget http://mary.dfki.de/download/5.1.2/marytts-installer-5.1.2.zip && unzip marytts-installer-5.1.2.zip && cd marytts-installer-5.1.2 && ./marytts install
```

## Setup MarryTTS in `~/.jasper/profile.yml`

⚠️ **Don't forget to add a voice**

Now you need to update your ~/.jasper/profile.yml:

```yaml
# Text To Speech Config default is espeak-tts
# uncomment to use
tts_engine: mary-tts

mary-tts:
  server: 'yourserverip'
  port: '59125'
  language: 'en_US'
  voice: 'cmu-slt-hsmm'
```

**chrobi.me public server config:**

```yaml
# Text To Speech Config default is espeak-tts
# uncomment to use
tts_engine: mary-tts

mary-tts:
  server: 'marytts.chrobi.me'
  port: '59125'
  language: 'en_US'
  voice: 'cmu-slt-hsmm'
```

**Better-Secured(https) to the server:**

```text
Coming Soon (code base update required).
```

# Voices for Marry TTS

Supported Languages **BOLD ARE CHOICES FOR profile.yml**:

## English

- **cmu-bdl-hsmm** :A male US English hidden semi-Markov model voice, built from recordings provided by Carnegie Mellon University

- **cmu-slt** :A female US English unit selection voice, built from recordings provided by Carnegie Mellon University

- **cmu-slt-hsmm** :A female US English hidden semi-Markov model voice, built from recordings provided by Carnegie Mellon University

- **cmu-rms-hsmm** :A male US English hidden semi-Markov model voice, built from recordings provided by Carnegie Mellon University

- **dfki-obadiah** :A male British English expressive unit selection voice: Gloomy Obadiah

- **dfki-obadiah-hsmm** :A male British English hidden semi-Markov model voice

- **dfki-poppy** :A female British English expressive unit selection voice: Cheerful Poppy

- **dfki-poppy-hsmm** :A female British English hidden semi-Markov model voice

- **dfki-prudence** :A female British English expressive unit selection voice: Pragmatic Prudence

- **dfki-prudence-hsmm** :A female British English hidden semi-Markov model voice

- **dfki-spike** :A male British English expressive unit selection voice: Aggressive Spike

- **dfki-spike-hsmm** :A male British English hidden semi-Markov model voice

## French

- **enst-camille** :A female French unit selection voice, built at Télécom ParisTech (ENST) using data recorded by Camille Dianoux

- **enst-camille-hsmm** :A female French hidden semi-Markov model voice, built at Télécom ParisTech (ENST) using data recorded by Camille Dianoux

- **enst-dennys-hsmm** :A male Québécois French hidden semi-Markov model voice, built at Télécom ParisTech (ENST)

- **upmc-jessica** :A female French unit selection voice, built at ISIR (UPMC) using data recorded by Jessica Durand

- **upmc-jessica-hsmm** :A female French hidden semi-Markov model voice, built at ISIR (UPMC) using data recorded by Jessica Durand

- **upmc-pierre** :A male French unit selection voice, built at ISIR (UPMC) using data recorded by Pierre Chauvin

- **upmc-pierre-hsmm** :A male French hidden semi-Markov model voice, built at ISIR (UPMC) using data recorded by Pierre Chauvin

## German

- **dfki-pavoque-neutral** :A male German unit selection voice

- **dfki-pavoque-neutral-hsmm** :A male German hidden semi-Markov model voice

- **dfki-pavoque-styles** :A male German unit selection voice with expressive styles "happy", "sad", "angry", and "poker"

- **bits1-hsmm** :A female German hidden semi-Markov model voice, built from voice recordings provided by the BITS project at the Bavarian Archive of Speech Signals

- **bits3** :A male German unit selection voice, built from voice recordings provided by the BITS project at the Bavarian Archive of Speech Signals

- **bits3-hsmm** :A male German hidden semi-Markov model voice, built from voice recordings provided by the BITS project at the Bavarian Archive of Speech Signals

## Italian

- **istc-lucia-hsmm** :Italian female Hidden semi-Markov model voice kindly made available by Fabio Tesser

## Turkish

- **dfki-ot** :A male Turkish unit selection voice

- **dfki-ot-hsmm** :A male Turkish hidden semi-Markov model voice

## Russian

- **voxforge-ru-nsh** :Russian male voice kindly made available by Nickolay V. Shmyrev

## Telugu

- **cmu-nk** :A female Telugu unit selection voice built from voice recordings provided by IIIT Hyderabad and Carnegie Mellon University

- **cmu-nk-hsmm** :A female Telugu hidden semi-Markov model voice built from voice recordings provided by IIIT Hyderabad and Carnegie Mellon University

<DocPreviousVersions/>
<EditPageLink/>
