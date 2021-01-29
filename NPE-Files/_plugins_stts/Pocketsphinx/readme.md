---
id: pocketsphinx
label: Pocketsphinx
title: Pocketsphinx - Speech to Text
type: stts
description: "This is an example readme for testing purposes"
logo: images/plugins/pocketsphinx.jpg
source: https://github.com/NaomiProject/naomi-docs/edit/dev/NPE-Files/_plugins_stts/Pocketsphinx/readme.md
meta:
  - property: og:title
    content: "Pocketsphinx - Speech to Text"
  - property: og:description
    content: "This is an example readme for testing purposes"
---

# Pocketsphinx - Speech to Text <Badge text="Included"/>

<PluginLogo/>

These instructions are for installing pocketsphinx on Raspbian Stretch.
They should translate to other Debian Stretch based distros like Ubuntu, Mint, etc pretty easily.
If you are comfortable with your system, you should be able to use these instructions with almost any distro.
In many cases the package names will be the same, and in other cases you should be able to locate the package
by searching for its name or the name of a file within it.

## test the microphone ("hello, can you hear me?")

You want to make sure that the level indicator at the bottom of the screen goes up to about 60% when you are speaking.
Use alsamixer to adjust your recording and playback levels.

Also, play it back and make sure the audio does not contain any hissing or popping.

We will use Phonetisaurus to prepare PocketSphinx to transcribe this audio later in these instructions.

```shell
[~]$ sudo apt install alsa-utils

[~]$ alsamixer

[~]$ arecord -vv -r16000 -fS16_LE -c1 -d3 test.wav

[~]$ aplay test.wav
```

If you are on a Raspberry Pi, most likely when you use the arecord command,
you will get an error such as "arecord: main:788: audio open error: No such file or directory".
This is because the first sound device (card 0) is output only. You will need to specify the
recording device. To get a list of recording devices, use "arecord -l". This will return something like this:

```shell
[~]$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: Phone [PH USB Speaker Phone], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

This means that audio card 1, subdevice 0 is capable of recording audio. Usually
you will either reference the device as hw:1,0 or plughw:1,0. hw:1,0 accesses the
device more directly, while plughw:1,0 includes a translation layer allowing it to
be used to record in formats that the device does not support natively. You can use
"arecord -L" to see which interfaces are available:

```shell
[~]$ arecord -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Phone
    PH USB Speaker Phone, USB Audio
    Default Audio Device
sysdefault:CARD=Phone
    PH USB Speaker Phone, USB Audio
    Default Audio Device
dmix:CARD=Phone,DEV=0
    PH USB Speaker Phone, USB Audio
    Direct sample mixing device
dsnoop:CARD=Phone,DEV=0
    PH USB Speaker Phone, USB Audio
    Direct sample snooping device
hw:CARD=Phone,DEV=0
    PH USB Speaker Phone, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Phone,DEV=0
    PH USB Speaker Phone, USB Audio
    Hardware device with all software conversions
```

Use "-D" to specify the device, and "--list-hw-params" to get more information about what formats the device supports:

```shell
[~]$ arecord -Dhw:1,0 --dump-hw-params
Recording WAVE 'stdin' : Unsigned 8 bit, Rate 8000 Hz, Mono
HW Params of device "hw:1,0":
--------------------
ACCESS:  MMAP_INTERLEAVED RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 32
CHANNELS: 2
RATE: 16000
PERIOD_TIME: [1000 8192000]
PERIOD_SIZE: [16 131072]
PERIOD_BYTES: [64 524288]
PERIODS: [2 1024]
BUFFER_TIME: [2000 16384000]
BUFFER_SIZE: [32 262144]
BUFFER_BYTES: [128 1048576]
TICK_TIME: ALL
--------------------
arecord: set_params:1299: Sample format non available
Available formats:
- S16_LE
```

The important bits here are "CHANNELS: 2", "RATE: 16000" and "Available formats: - S16_LE".
The rate and format match the format that Naomi expects audio to be captured in, but we need
mono audio, not stereo, so we will most likely need to use the plughw version.

```shell
[~]$ arecord -Dhw:1,0 -vv -r16000 -fS16_LE -c1 -d3 test.wav
Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 16000 Hz, Mono
arecord: set_params:1305: Channels count non available

[~]$ arecord -Dplughw:1,0 -vv -r16000 -fS16_LE -c1 -d3 test.wav
Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 16000 Hz, Mono
```

# Install Phonetisaurus

## Build and install openfst

```shell
[~]$ sudo apt install gcc g++ make python-pip autoconf libtool
[~]$ wget http://www.openfst.org/twiki/pub/FST/FstDownload/openfst-1.6.9.tar.gz
[~]$ tar -zxvf openfst-1.6.9.tar.gz
[~]$ cd openfst-1.6.9
[~/openfst-1.6.9]$ autoreconf -i
[~/openfst-1.6.9]$ ./configure --enable-static --enable-shared --enable-far --enable-lookahead-fsts --enable-const-fsts --enable-pdt --enable-ngram-fsts --enable-linear-fsts --prefix=/usr
[~/openfst-1.6.9]$ make
[~/openfst-1.6.9]$ sudo make install
[~/openfst-1.6.9]$ cd
```

## Build and install mitlm-0.4.2

Building mitlm is only necessary because we are training our own fst model a little further on.

```shell
[~]$ sudo apt install git gfortran autoconf-archive
[~]$ git clone https://github.com/mitlm/mitlm.git
[~]$ cd mitlm
[~/mitlm]$ ./autogen.sh
[~/mitlm]$ make
[~/mitlm]$ sudo make install
[~/mitlm]$ sudo ldconfig
[~/mitlm]$ cd
```

## Build and install Phonetisaurus

If you used the naomi-setup.sh script and chose option 1 (Use virtualenvwrapper to create a virtual Python 3 environment
for Naomi) you will need to activate the Naomi virtual environment at this time (if you haven't already)
```shell
[~]$ workon Naomi
(Naomi)[~]$
```

Now go ahead and install Phonetisaurus
```shell
[~]$ pip install pybindgen
[~]$ git clone https://github.com/AdolfVonKleist/Phonetisaurus.git
[~]$ cd Phonetisaurus
[~/Phonetisaurus]$ ./configure --enable-python
[~/Phonetisaurus]$ make
[~/Phonetisaurus]$ sudo make install
[~/Phonetisaurus]$ cd python
[~/Phonetisaurus/python]$ cp -iv ../.libs/Phonetisaurus.so ./
```
Only use sudo while installing the python module if you are NOT using a
virtual environment.
```
(Naomi) [~/Phonetisaurus/python]$ python setup.py install
```
or
```
[~/Phonetisaurus/python]$ sudo python setup.py install
```
finally:
```
[~/Phonetisaurus/python]$ cd
```

# Build and install CMUCLMTK

```shell
[~]$ sudo apt install subversion
[~]$ svn co https://svn.code.sf.net/p/cmusphinx/code/trunk/cmuclmtk/
[~]$ cd cmuclmtk
[~/cmuclmtk]$ ./autogen.sh
[~/cmuclmtk]$ make
[~/cmuclmtk]$ sudo make install
[~/cmuclmtk]$ sudo ldconfig
[~/cmuclmtk]$ cd
[~]$ sudo pip install cmuclmtk
```

# Install Pocketsphinx

## Build and install sphinxbase

```shell
[~]$ sudo apt install swig libasound2-dev bison
[~]$ git clone --recursive https://github.com/cmusphinx/pocketsphinx-python.git
[~]$ cd pocketsphinx-python/sphinxbase
```
Now, the next line will be different depending on where your python library is located.

If you used the naomi-setup.sh script to install Naomi and chose option 1 (Use virtualenvwrapper to create a virtual Python 3 environment
   for Naomi), it will look something like this:
```shell
[~/pocketsphinx-python/sphinxbase]$ workon Naomi
(Naomi)[~/pocketsphinx-python/sphinxbase]$ PYTHON="$(which python)" PYTHON_VERSION=$(python --version | sed -E 's/^Python ([[:digit:]]+\.[[:digit:]]+)\.[[:digit:]]+$/\1/') ./autogen.sh LDFLAGS="-L$(which python| sed -E 's/\/bin\/python$/\/lib/')"
```

If you used the naomi-setup.sh script to install naomi and chose option 2 (Download, compile, and install a local copy of Python for Naomi)
```shell
[~/pocketsphinx-python/sphinxbase]$ PYTHON="/home/pi/.config/naomi/local/bin/python" PYTHON_VERSION=$(/home/pi/.config/naomi/local/bin/python --version | sed -E 's/^Python ([[:digit:]]+\.[[:digit:]]+)\.[[:digit:]]+$/\1/') ./autogen.sh LDFLAGS="-L/home/pi/.config/naomi/local/lib"
```

If you installed directly on your base python using apt, then you probably just need
```shell
[~/pocketsphinx-python/sphinxbase]$ PYTHON="$(which python3)" PYTHON_VERSION=$(python3 --version | sed -E 's/^Python ([[:digit:]]+\.[[:digit:]]+)\.[[:digit:]]+$/\1/') ./autogen.sh
```

Moving on:
```shell
[~/pocketsphinx-python/sphinxbase]$ make
[~/pocketsphinx-python/sphinxbase]$ sudo make install
[~/pocketsphinx-python/sphinxbase]$ cd ..
```

## Build and install pocketsphinx

```shell
[~/pocketsphinx-python]$ cd pocketsphinx
```
Again, the next line will be different depending on where your python library is located.

If you used the naomi-setup.sh script to install Naomi and chose option 1 (use virtualenvwrapper), it will look something like this:
```shell
(Naomi)[~/pocketsphinx-python/sphinxbase]$ PYTHON="$(which python)" PYTHON_VERSION=$(python --version | sed -E 's/^Python ([[:digit:]]+\.[[:digit:]]+)\.[[:digit:]]+$/\1/') ./autogen.sh LDFLAGS="-L$(which python| sed -E 's/\/bin\/python$/\/lib/')"
```

If you used the naomi-setup.sh script to install Naomi and chose option 2 (install a local copy of Python), it will look something like this:
```shell
[~/pocketsphinx-python/sphinxbase]$ PYTHON="/home/pi/.config/naomi/local/bin/python" PYTHON_VERSION=$(/home/pi/.config/naomi/local/bin/python --version | sed -E 's/^Python ([[:digit:]]+\.[[:digit:]]+)\.[[:digit:]]+$/\1/') ./autogen.sh LDFLAGS="-L/home/pi/.config/naomi/local/lib"
```

If you installed directly on your base python using apt, then you probably just need
```shell
[~/pocketsphinx-python/sphinxbase]$ PYTHON="$(which python3)" PYTHON_VERSION=$(python3 --version | sed -E 's/^Python ([[:digit:]]+\.[[:digit:]]+)\.[[:digit:]]+$/\1/') ./autogen.sh
```
Moving on:
```shell
[~/pocketsphinx-python/pocketsphinx]$ make
[~/pocketsphinx-python/pocketsphinx]$ sudo make install
[~/pocketsphinx-python/pocketsphinx]$ cd ..
```

## Install python PocketSphinx library

Again, you may need to adjust this line depending on the location of your python executable.

If you installed using naomi-setup.py and selected option 1 (virtualenvwrapper):
```shell
(Naomi)[~/pocketsphinx-python]$ python setup.py install
```

If you installed using naomi-setup.py and selected option 2 (custom Python):
```
[~/pocketsphinx-python]$ ~/.config/naomi/local/bin/python setup.py install
```

Otherwise:
```shell
[~/pocketsphinx-python]$ sudo python3 setup.py install
```

## Format cmudict.dict and train model.fst

I'm not exactly sure why this is, but apparently it is necessary to reformat the default cmudict.dict file.

* When there are multiple pronunciations for a word, this removes the trailing "(n)".
* Then it compresses multiple white spaces into a single space.
* Then it removes white space from the beginning and end of the line.
* Finally, it replaces the first space on the line with a tab character.

```shell
[~/pocketsphinx-python]$ cd pocketsphinx/model/en-us
[~/pocketsphinx-python/pocketsphinx/model/en-us]$ cat cmudict-en-us.dict | perl -pe 's/^([^\s]*)\(([0-9]+)\)/\1/;s/\s+/ /g;s/^\s+//;s/\s+$//;s/[\}\|\_]/ /g;@_=split(/\s+/); $w=shift(@_);$_=$w."\t".join(" ",@_)."\n";' > cmudict-en-us.formatted.dict
[~/pocketsphinx-python/pocketsphinx/model/en-us]$ phonetisaurus-train --lexicon cmudict-en-us.formatted.dict --seq2_del
[~/pocketsphinx-python/pocketsphinx/model/en-us]$ cd
```

## Test

```shell
[~]$ mkdir test
[~]$ cd test
[~/test]$ echo "<s> hello can you hear me </s>" > test_reference.txt
```

## Create test.vocab

```shell
[~/test]$ text2wfreq < test_reference.txt | wfreq2vocab > test.vocab
```
if you get errors like text2wfreq not found or wfreq2vocab not found, go back and reinstall cmuclmtk.

## Create test.idngram

```shell
[~/test]$ text2idngram -vocab test.vocab -idngram test.idngram < test_reference.txt
```

## Create test.lm

```shell
[~/test]$ idngram2lm -vocab_type 0 -idngram test.idngram -vocab test.vocab -arpa test.lm
```

## Create test.formatted.dict

```shell
[~/test]$ phonetisaurus-g2pfst --model=`ls ~/pocketsphinx-python/pocketsphinx/model/en-us/train/model.fst` --nbest=1 --beam=1000 --thresh=99.0 --accumulate=true --pmass=0.85 --nlog_probs=false --wordlist=./test.vocab > test.dict
[~/test]$ cat test.dict | sed -rne '/^([[:lower:]])+\s/p' | perl -pe 's/([0-9.])+//g;s/\s+/ /g;@_=split(/\s+/);$w=shift(@_);$_=$w."\t".join(" ",@_)."\n";' > test.formatted.dict
```

## Test with audio file

```shell
[~/test]$ pocketsphinx_continuous -hmm ~/pocketsphinx-python/pocketsphinx/model/en-us/en-us -lm ./test.lm -dict ./test.formatted.dict -samprate 16000/8000/48000 -infile ~/test.wav 2>/dev/null
```

## Test with microphone

```shell
[~/test]$ pocketsphinx_continuous -hmm ~/pocketsphinx-python/pocketsphinx/model/en-us/en-us -lm ./test.lm -dict ./test.formatted.dict -samprate 16000/8000/48000 -inmic yes 2>/dev/null
```

Here's what this section of the profile.yml looks like

```shell
active_stt:
  engine: sphinx
pocketsphinx:
  fst_model: /home/pi/pocketsphinx-python/pocketsphinx/model/en-us/train/model.fst
  hmm_dir: /home/pi/pocketsphinx-python/pocketsphinx/model/en-us/en-us
  phonetisaurus_executable: phonetisaurus-g2pfst
```


<EditPageLink/>
